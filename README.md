# DevOp-Enviroment
Setting up a testing enviroment for your webapps.



1- Download Rasberry pi imager from the offical website.
2- Create a bootable sd using the Rasperri pi os LITE.
3- sudo raspi-config to get to the option setups 
  expand file system
  enable ssh
  change password
  update 
  Finally, $ sudo reboot
  

Conntect to internet : 

$sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
Add the following : 
network={
    ssid="testing"
    psk="testingPassword"
}

  


Reconfigure the interface with 
$ wpa_cli -i wlan0 reconfigure.



  
$ sudo update-ca-certificates
$ sudo apt-get update 
$ sudo apt-get upgrade -y 
$ sudo apt-get dist-upgrade -y





ifconfig wlan0 to find your IP and confirm your connection

You may now use $ shh pi@<IP address>  to connect to your rasberry pi from any other devce on your network.
 
 
 

# Making a public server


1- Installing Apache

$ sudo apt-get install apache2 php5 libapache2-mod-php5

If you get any errors, run the following commands: 
$ sudo groupadd www-data 
$ sudo usermod -g www-data www-data 

Restart Apache with the following command: 

$ sudo service apache2 restart




# Assuming you have your application files ready ( python files in this case )

$ sudo apt-get install nginx
$ sudo apt-get install python3-pip
$ sudo pip3 install flask uwsgi




Once you test your app you may use 

$ uwsgi --socket 0.0.0.0:8081 --protocol=http -w <name of your starting point>:app


4- For an extra layer of security install fail2ban. Fail2Ban blocks suspicious requests coming from the internet. For example, if there are too many attempts to guess the password, it will block that IP address. It can be installed by typing into terminal: $ sudo apt-get install fail2ban
