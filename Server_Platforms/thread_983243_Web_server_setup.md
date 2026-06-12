---
title: "Web server setup"
date: 2008-11-15
forum: Server Platforms
---

### Post by adman4054 on 2008-11-15
I'm new to Ubuntu and need some setup help. I'm currently running a server with IIS, Windoze 2003 and I host about 65 websites on that box. I want to setup the Ubuntu box to perform the same tasks as my Windoze box. I've set it (8.04) up as a LAMP server and installed all the necessary components, but I'm not clear on the setup of apache and a few other items. 
I received this information from my co-lo, should this info be placed in httpd.conf file? If so, what other information should be placed in that file to correctly serve pages? Should there be any reference to the local host?
IP3: 000.00.00.00

IP4: 000.00.00.00

Netmask: 000.000.000.000

Gateway: 000.00.00.00

 

Primary DNS: 000.00.000

Secondary DNS: 00.000.0.000


My next question has to do with remote access. I have enabled it per the instructions, but I'm not clear on how to access the box remotely and if I need any other components or settings. On the Windows box I connect with an IP address and user/pass combination and I'm at the desktop. I want to do the same with this server. I do have the desktop gui installed.

Firewall, with just operating a web/db server, should I use "uncomplicated", "Firestarter" or? 

FTP server-- I use bulletproof ftp server on my Windoze box. This allows for me to add users on a particular website and allows me to deny ip addresses after two unsuccessful attempts at logging in. Is vsftpd the best option for this kind of setup?

Anything I'm missing? Any suggestions?

I'm really impressed with Ubuntu and I think once I can get it setup properly the rest should be a breeze.
Thanks in advance:)

---

### Post by Philio on 2008-11-15
Well for starters you shouldn't run a GUI on a server it will introduce potential security issues. It also gives you absolutely no advantage over using a shell as you are performing the exact same tasks as you would anyway in the shell.

If your not comfortable configuring Linux you might want to consider some easier alternatives:

1. Installing a control panel such as Webmin.
2. Switch to CentOS with cPanel.
3. Stick to Windows.

To admin your server you need to login via SSH, either with 'ssh 1.2.3.4' from Linux or using something like Putty in Windows.

Basic steps to setup LAMP hosting for multiple accounts would be something like this (note replace 1.2.3.4 with your IP and mydomain.com with the domain you want to use):

1. Create a user account and home directory using the useradd command

e.g. useradd -m mydomain.com

2. Set a password for your account

e.g. passwd mydomain.com

3. Create a folder in the user's home directory for web root 

e.g. mkdir /home/mydomain.com/www

4. Create a new file  /etc/apache2/sites-available/mydomain.com and put in VirtualHost directives 

e.g.
<VirtualHost 1.2.3.4:80>
    ServerName mydomain.com
    ServerAlias [www.mydomain.com](www.mydomain.com)
    DocumentRoot /home/mydomain.com/www
</VirtualHost>

You also need to include once (per IP) only somewhere in the config files:

NameVirtualHost 1.2.3.4:80

5. Enable your new domain using a2ensite command or simply sym-link from /etc/apache2/sites-available to /etc/apache2/sites-enabled with:

ln -s /etc/apache2/sites-available/mydomain.com /etc/apache2/sites-enabled/

6. Restart Apache with /etc/init.d/apache2 restart

7. Assuming you have DNS setup correctly to point at the server, check your new site works! You should at least get a 404 if there is nothing in the www directory (or whatever name you used for the web folder).

vsftp will work perfectly with this setup with little/no config changes, you might want to enable chroot.

Not sure which is the best firewall for Ubuntu as never used one as we use hardware firewalls.

Hope this helps :)

---

### Post by Iowan on 2008-11-16
8.04.1 comes with **ufw** as default firewall.

---

### Post by Francewhoa on 2009-06-29
The easiest way I know of to setup a web server on Ubuntu is Virtualmin, Webmin & Usermin. They are free and open source like Ubuntu.

I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing Virtualmin, Webmin & Usermin.

---

### Post by TwiceOver on 2009-06-29
Just to be sure, are any of these 65 sites you host based on ASP?  That's kinda going to be a problem.

EDIT:  Didn't realize this post was 6 months old.. Sorry.

---

