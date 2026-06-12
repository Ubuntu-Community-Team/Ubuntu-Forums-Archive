---
title: "Apache web server to share a directory"
date: 2008-06-09
forum: Server Platforms
---

### Post by tars16 on 2008-06-09
Hi Guys,

I'm pulling my hair out over here.  I'm trying to setup an apache webserver to share a directory of files over the internet.  I want to setup a username and password so that only those with access can use it.

I did this on my windows machine by installing apache2 web server and sharing a single directory and using an .htaccess file.

I can't figure out how to do this with ubuntu and i'm switching from windows because I thought it was easier and more stable?

I've got apache installed... going to local host says "it works!"  Everything i'm finding is telling me i need to install php and mysql, i don't want to host a website... just share a directory.  Please help!  The directory i want to share is on a second hard disk, i can't even figure out the direct path to it :(  I navigate to it by hitting /media/disk/ but that doesn't work in my config files?

Thanks for any input you guys have.

---

### Post by azurepancake on 2008-06-09
I'm afraid I am not knowledgeable enough to help you out with sharing files via HTTP. 

But, I would like to recommend using FTP. I use "vsftpd" and it can do exactly what you'd like to do and more!

With FTP, you simply set the directory you want to be shared over the internet as "home", type in the IP address or domain name ([ftp://myftpsite.org](ftp://myftpsite.org)) and your directory and its sub-directories will be listed. Using permissions you can make it quite secure.  

Here is a awesome guide for setting up vsftpd - [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)

Hope this helps!

---

### Post by hyper_ch on 2008-06-10
where does it tell you to install php?

And just alter the documentroot in the apache config to the according directory

---

### Post by talikarng on 2008-08-23
> **hyper_ch said:**
> And just alter the documentroot in the apache config to the according directory

How do you do this?
I would like to be able to get to the point where I have read/write access to the folder from anywhere on my local network (with a password).
I understand that you can use Samba but I do not wish to set this up on multiple computers.

---

### Post by windependence on 2008-08-23
You need to turn on Directory listings in Apache. You do NOT have to install php or MySQL no matter what anyone tells you.

Put this in your /etc/apache2.conf and restart Apache:

<Directory /var/www>
Options Indexes FollowSymLinks
</Directory>

Make sure you remove any index.html files in /var/www.

-Tim

---

