---
title: "Webmin Lamp needs GD Lib"
date: 2009-07-10
forum: Server Platforms
---

### Post by leona on 2009-07-10
Hi

I have build a Ubuntu 8.04 Lamp Server using Webmin, this is a virtual server to replace my windows 2000 physical box.

So far I have got most things up and running, a few things are different to what I am used to so am working my way around.

One thing I do need working is the GD Library.

I have tried installing this via apt-get install php5-gd, this did install, but still when I look at the phpinfo screen, no GD library can be found.

So how do I go about installing and configuring the GD lib.

In windows, all I did was edit the php.ini file and remove a comment next to the library I wanted, seems that Linux doesn't work like that and I am unable to see how I enable this library.

Can someone help me please.

Leona.

---

### Post by credobyte on 2009-07-10
I might sound stupid, but .. have you restarted your server ( apache ) ?

---

### Post by leona on 2009-07-10
Not a silly suggestion, but yes I have done that, but sadly still no GD :(

---

### Post by leona on 2009-07-10
Does anyone have any more suggestions?

---

### Post by credobyte on 2009-07-10
Verify gd.so existence :
```
cd /usr/lib/php5/20060613+lfs && ls -l
```Open php.ini :
```
sudo gedit /etc/php5/apache2/php.ini
```Add this line :
```
extension=gd.so
```
Restart Apache :
```
sudo /etc/init.d/apache2 restart
```Give it a try ;)

---

### Post by leona on 2009-07-10
Hi, thank you, I verified the directory was there, I added the extension to the pho.ini file, restarted the Virtual Server, but sadly still no sign of the GD Library :(

---

### Post by leona on 2009-07-11
Actually that dir you gave doesn't have gd.so in it, so does this mean the apt-get install php5-gd didn't work?

I am still not having much luck here,

Right, got it working, I re ran the apt-get install php5-gd line and this time it worked, I do not know why it didn't work the first time, but it is now working.

Thank you all

---

