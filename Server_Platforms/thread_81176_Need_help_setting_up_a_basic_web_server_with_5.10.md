---
title: "Need help setting up a basic web server with 5.10"
date: 2005-10-23
forum: Server Platforms
---

### Post by wildscribe on 2005-10-23
I am happy to see that Ubuntu has released a server version. From what I can see it is a stripped down version of the desktop, but that is fine with me. 

Now, I need to figure out how to download the necessary software required for a server running Apache, PHP 5, MySQL, SSH, and FTP. 

So far, I figured out this much:

sudo apt-get install apache2   // installs Apache 2 server
sudo apt-get install php         // installs PHP 5
sudo apt-get install ssh         // installs SSH server

I cannot figure out how to use apt-get to download and install 
MySQL, an FTP server (not sure which FTP server program is available 
and is there an SFTP server offered?)

I also need to know which file I need to edit to set up a static IP 
address and which apache file I need to edit to set up virtual 
web sites.

Thanks to all!

- - - Wild

---

### Post by dbee on 2005-10-23
Try 

sudo apt-cache --names-only search mysql

or else try

aptitude 

the apache file is 

httpd.conf 

in the config directory (whereever synaptic has put the config directory)

as for the static IP, not too sure but I'd imagine 

/etc/hosts
/etc/network/interfaces

good luck

---

### Post by dbee on 2005-10-24
also check out this tutorial OP

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

it should guide you through the setup

---

### Post by LordHunter317 on 2005-10-24
You need to (IIRC) enable the universe repositority to install MySQL.  Edit /etc/apt/sources.list and update as appropriate.

---

### Post by wildscribe on 2005-10-24
Excellent! Thank you all for helping me out!

- - - Wild

---

