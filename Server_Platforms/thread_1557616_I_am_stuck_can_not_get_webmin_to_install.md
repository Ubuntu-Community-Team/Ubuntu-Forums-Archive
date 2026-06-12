---
title: "I am stuck can not get webmin to install"
date: 2010-08-21
forum: Server Platforms
---

### Post by Bushcraft Bill on 2010-08-21
I can get on the server from my laptop cool! putty works

when installing webmin their are 3 files that it wants I try and get them but they seem to not want to install and ask that they be installed with the -f did that but those files will still not install.. 
what do I do now?

I have attached a pic it may or may not help you to figure out what is going on...I did try a few few things 

I am so close!

when I plugged in the ip the message said it works but no web content 

when I put in the :10000 in after the IP I get the unable to connect message..is this because webmin is not installed?

---

### Post by silbak04 on 2010-08-21
you need to install all the dependencies for webmin...which is what it says to do...like for example it tells you to install libnet-ssleay-perl...so if you were to do this in the terminal ```
$ sudo aptitude install libnet-ssleay-perl
``` this will install one of the dependencies...just install all of them from what it tells you...and try again, and let me know if that works

---

### Post by Bushcraft Bill on 2010-08-21
ok that seems to work when I add in the aptitude thing I did not see that bit of info anywhere... will do the other files that way and see how that goes... thanks!

> **silbak04 said:**
> you need to install all the dependencies for webmin...which is what it says to do...like for example it tells you to install libnet-ssleay-perl...so if you were to do this in the terminal ```
$ sudo aptitude install libnet-ssleay-perl
``` this will install one of the dependencies...just install all of them from what it tells you...and try again, and let me know if that works

---

### Post by wojox on 2010-08-21
May help [Installing Webmin on Ubuntu Server 10.04 LTS (Lucid)]("http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/")

---

### Post by Bushcraft Bill on 2010-08-21
well Ill be damn it works thanks that one command was the key to it all that should be added into the manual....

---

### Post by kevinthecomputerguy on 2010-08-22
Bushcraft Bill-
I was looking at your screen shot, and it was asking you to run apt-get install -f with no packages.
 
That would look like this:
 
apt-get install -f
 
I know you have what you need already, but incase you run into that again, that message means to type that command without any package names afterwards.
 
Also the first error in your printscreen as asking you to type about 5 package names, not just that one. After getting those 5 other packages, it would have continued the webmin install for you.
 
again, incase you ever run into that again.
 
 
-Kevin

---

### Post by Bushcraft Bill on 2010-08-22
thanks

---

