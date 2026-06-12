---
title: "Owncloud and hardening Apache"
date: 2014-09-15
forum: Security
---

### Post by mr-woof on 2014-09-15
Hi all,

I'm thinking about setting up an OwnCloud instance and I'm after some advice on hardening the server, before I expose it to the badness that is the internet.

I wasn't sure if this was a security question or a server question, so op's please move if you feel this is in the wrong place.

At the moment, I'm just playing around with some virtual machines on my laptop as I google/work through all the guides and recommendations, but I'll post what I've been upto and if anyone can amend / add anything please post. 

**Install server and OwnCloud**

The server is ubuntu 14.04, updated and fully patched, first install owncloud:

sudo apt-get install owncloud
sudo apt-get install mysql-server

run the mysql_secure_installation command and with the following yes/no's

Set root password? [Y/n] y
Remove anonymous users? [Y/n] y
Disallow root login remotely? [Y/n] y
Remove test database and access to it? [Y/n] y
Reload privilege tables now? [Y/n] y

mysql -u root -p
Enter password:

mysql> CREATE USER 'user'@'localhost' IDENTIFIED BY 'SOMEPASSWORD';
mysql> CREATE DATABASE ownclouddb;
mysql> GRANT ALL ON ownclouddb.* TO 'user'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> exit

and it's installed now on [http://ip/owncloud](http://ip/owncloud)

**Hardening Apache:**

I've set it to hide the version and OS

sudo nano /etc/apache2/conf-enabled/security.conf

ServerTokens Prod
ServerSignature Off
TraceEnable Off

Set it to use HTTPS instead of http

sudo a2enmod ssl
sudo service apache2 restart
sudo mkdir /etc/apache2/ssl

sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt

edit the owncloud conf file

sudo nano /etc/apache2/conf-enabled/owncloud.conf

<VirtualHost 192.168.1.100:443>
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.crt
SSLCertificateFileKey /etc/apache2/ssl/apache.key

add </VirtualHost> underneath </Directory>

sudo service restart apache2

I've also deleted the default index.html file in /var/www.

**Hardening PHP:**

one of the guides advised that you should make a few changes to PHP, so:

sudo nano /etc/php5/apache2/php.ini 

    Add exec, system, shell_exec, and passthru to disable_functions.
    Change expose_php to Off.
    Ensure that display_errors, track_errors and html_errors are set to Off.


I've also installed Fail2Ban and ACCT, the next thing I'm going to play with is Mod Security and Mod Evasive.

If this does go live, it'll be behind a smoothwall firewall with restrictions of whats going in and going out, so I've not included any IPtables/UFW bits as yet.

What do you all think so far? What else can I do to Apache?

---

### Post by Habitual on 2014-09-15
Add [http://doc.owncloud.org/server/6.0/admin_manual/apps/files_encryption/](http://doc.owncloud.org/server/6.0/admin_manual/apps/files_encryption/) to the mix.
Disable root access via ssh to the server.
Use ssh-keys.

---

### Post by mr-woof on 2014-09-16
The encryption looks good, I'll get that set up thanks for the link.

Sorry I should of mentioned I'm good for securing SSH with Keys etc, any other ideas on the Apache front ? :)

---

### Post by Habitual on 2014-09-16
The only other restriction I would use is 
deny from all
allow from <ip0>

in the apache conf file.

Just to keep the "accidental" hacker/script kiddie out.

Is this site to be limited to just personal use?
If not, you can also specify multiple 
allow from <ip1>
allow from <ip2>
etc...

---

### Post by mr-woof on 2014-09-17
Hi Habitual,

thanks that's not a bad idea, I'll have a look at that today at the moment I'm still playing around with it to see if I can actually make use of use it.

One guy mentioned that he had setup a vpn, and then connected to it that way so not exposing it to the internet at all which could be an idea.

---

### Post by Habitual on 2014-09-17
VPN is a good idea also. ;)

---

