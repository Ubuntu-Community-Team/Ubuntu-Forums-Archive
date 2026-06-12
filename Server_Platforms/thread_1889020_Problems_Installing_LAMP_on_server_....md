---
title: "Problems Installing LAMP on server ..."
date: 2011-11-30
forum: Server Platforms
---

### Post by jaesun on 2011-11-30
This is kind of long, but wanted to be thorough. I am trying to install LAMP on the Ubuntu Server to setup my own local LAMP box on the network.  But once I finish everything, whenever I go to a php page, it prompts for a download.  I think have tried everything to make sure every I did all the steps right.  Not sure what is going wrong or if I missed something?

Information:
- Installing on a VM, Oracle VirtualBox (Created new VM using default settings, Linux Ubuntu 64 Bit).  I have the VM using a bridged network connection, with its own static IP set (set in the router)
- Ubuntu Server 11.10 64-bit, barebones install, did not install LAMP or anything else during the Ubuntu Install.

Steps I took:

Once logged in, I installed LAMP, using this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

$: sudo apt-get install tasksel
# tasksel looked to already have been installed
$: sudo tasksel install lamp-server

Once I did that, I setup apache.

I then setup the public_html directory.  But I have that elsewhere on the network.  So I Installed Samba, mounted the share at /mnt/localwww, then went into my /etc/fstab file and had it auto mount on boot

//192.168.1.101/www-dev /mnt/localwww smbfs username=USERNAME,password=PASSWORD, 0 0

Then I created a symbolic link to the mount to the public_html directory

$: ln -s /mnt/localwww /home/jaesun/public_html

From there, I setup apache2, using this:
[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

$: cd /etc/apache2/mods-enabled
$: sudo ln -s ../mods-available/userdir.conf userdir.conf
$: sudo ln -s ../mods-available/userdir.load userdir.load
$: sudo /etc/init.d/apache2 restart

I modified my host file in my own machine, to point to the Ubuntu server (statically set to 192.168.1.104), so that [http://dev/](http://dev/) will go to my local LAMP server.

I then went to /etc/apache2/sites-available and created a VirtualHost entry

$: cd /etc/apache2/sites-available
$: vi dev

and input this:

```
<VirtualHost *:80>
    ServerName dev
    DocumentRoot /home/jaesun/public_html
</VirtualHost>
```

then:

$: cd /etc/apache2/sites-enabled
$: sudo ln -s ../sites-available/dev dev
$: sudo /etc/init.d/apache2 restart

Lastly, I then went to /etc/apache2/ directory, and modified httpd.conf (I have done this to apache2.conf also) to add this:

```
<FilesMatch \.php$>
    SetHandler application/x-httpd-php
</FilesMatch>
```

then

$: sudo /etc/init.d/apache2 restart

Tested it out, got the php download prompt.

Found:
[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

$: sudo a2enmod php5
# Stated that this library was already enabled, I restarted apache anyways
$: sudo /etc/init.d/apache2 force-reload

Cleared out my browser history/cache.

[http://dev/test.php](http://dev/test.php)

Still got the download prompt.

**So this is where I am now currently**.  I have installed Ubuntu Server twice in VM, first time, installing LAMP Server during the install, and the second time, doing a barebones install, both times, getting the same results with the download prompt.  

I can view html files fine, view directories in the home directory.  But once I view a php file, it prompts to save the download.  

I am pretty sure php is installed.  I can go to the command line, and do 

$: php /home/jaesun/public_html/test/test.php 

and it'll output the php/html in test.php (<? echo 'test'; ?> hi)

Did I miss a step somewhere?  Am I doing something wrong?  Almost wanted to throw the monitor out the window!  Any help would be appreciated

---

### Post by jaesun on 2011-12-01
So I was messing around more with this.

php/apache default public_html directory is /var/www/ .  It has that index.html file with
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

I added a test.php file, and pointed my browser to:
[http://192.168.1.104/test.php](http://192.168.1.104/test.php)

and it works!  

wtf?  So maybe there something weird with the symbolic link in my VirtualDirectory setup (where above, I created [http://dev/](http://dev/) with it located at /home/jaesun/public_html)

I create another sym-link in /var/www (/var/www/test) to point to the same location that /home/jaesun/public_html is pointing to, and then test a file there [http://192.168.1.104/test/test.php](http://192.168.1.104/test/test.php)) and it works!

So
[http://dev/test.php](http://dev/test.php) prompts for download
[http://192.168.1.104/test/test.php](http://192.168.1.104/test/test.php) works

both are the same file.  

Is there something wrong that I did with the virtual users setup (creating a VirtualHost,etc) and enabling it in sites-enabled ??

**Edit1:**

If I go to my /etc/apache2/sites-available/dev and change the VirtualHost

from:
```
<VirtualHost *:80>
    ServerName dev
    DocumentRoot /home/jaesun/public_html
</VirtualHost>
```

to:
```
<VirtualHost *:80>
    ServerName dev
    DocumentRoot /var/www/test
</VirtualHost>
```

[http://dev/test.php](http://dev/test.php) works

So something is weird with having the DocumentRoot being at /home/jaesun/public_html ?  Every test I seem to throw at seems to point to problems whenever the public_html directory is used at /home/jaesun/, but if I use /var/www/ it seems to work.

---

