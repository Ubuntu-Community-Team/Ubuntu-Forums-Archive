---
title: "php5 setup help - undefined function ImageCreate()"
date: 2006-09-30
forum: Server Platforms
---

### Post by cpjeffl on 2006-09-30
Hi all-

I recently installed the Ubuntu LAMP server for my personal website.  In part of my php I am getting the error:

Fatal error: Call to undefined function ImageCreate() in /var/www/thermometer.php on line 14

looking around on Google, I found this related article:

[http://www.modwest.com/help/kb5-100.html](http://www.modwest.com/help/kb5-100.html)

I tried the suggestion to uncomment the line extension = gd.so  in my php.ini file but it did not help.  (I changed the php.ini file found at /etc/php5/apache2/php.ini)

I would really appreciate any help.  I am new to linux, so please err on the side of detail in any of your answers.

Thanks!

---

### Post by paul.maddox on 2006-09-30
You will probably need to install the GD module before trying to enable it


Try this:

sudo apt-get install php5-gd

---

### Post by cpjeffl on 2006-10-01
That fixed it.  Thank you very much!

For some reason I was under the impression that it would already be installed with php5.  Thanks for clearing that up.

---

### Post by got_nix on 2006-10-01
Nah gd libraries are different from base / core php5 files

---

### Post by ckoester on 2006-12-15
I'm getting the following error from Mediawiki when trying to resize images:

**Incomplete GD library configuration: missing function imagecreatefromjpeg**

I have installed the GD Module for PHP5 and uncommented extension = gd.so in php.ini.  When I view phpinfo() it says that the GD extension is enabled.

The Apache2 error log gives the following error:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/gd.so' - /usr/lib/php5/20051025/gd.so:  cannot open shared object file

---

### Post by ckoester on 2006-12-18
The solution for me was to uncomment the following line in the php.ini file:

**extension_dir = "./"**

It should be located at line# 461.  The line specifies where PHP should look for PHP modules.

---

### Post by LightShear on 2006-12-18
I just started getting php, but I'll try to help. After you uncommented that line, did you restart apache? In the command line type:
/etc/init.d/apache2 restart

Hope that helps,
Chris

Edit: I didn't see all the replies below! Disregard this one.

---

### Post by Fhernd on 2008-07-17
How do you do?

*sudo apt-get install php5-gd*, solved my problem with: **Fatal error**: Call to undefined function imagecreate() in **/var/www/studentsinaction/3901_phpya-excs.php** on line **4**


I will you later! Thank you!

---

