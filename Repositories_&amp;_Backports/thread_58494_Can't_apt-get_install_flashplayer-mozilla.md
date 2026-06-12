---
title: "Can't apt-get install flashplayer-mozilla"
date: 2005-08-20
forum: Repositories &amp; Backports
---

### Post by aquaboot on 2005-08-20
Hello,

I'm having trouble getting flashplayer.  I've done apt-get update and my sources list file queries these repositories:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
eb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

When I search for flash, I get:

root@darklight:~ # apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
root@darklight:~ # apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages [38.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [11.2kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Fetched 83.9kB in 3s (26.0kB/s)
Reading package lists... Done
root@darklight:~ # apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
root@darklight:~ #


Thanks in advance,

aquaboot

---

### Post by keyshawn on 2005-08-20
hey aquaboot, 

for the following lines:


 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted

you need to add "multiverse" to your sources list. If you don't know how to edit the list, use the command:
 ```
 sudo gedit /etc/apt/sources.list

``` 
[or substitute gedit whatever text editor you prefer]

then of course, update your lists and you should be good to go ! 

regards, 
keyshawn

---

### Post by heimo on 2005-08-20
apt-cache search ^libflash
 ```
libflash-dev - GPL Flash (SWF) Library - development files
libflash-mozplugin - GPL Flash (SWF) Library - Mozilla-compatible plugin
libflash-swfplayer - GPL Flash (SWF) Library - stand-alone player
libflash0c2 - GPL Flash (SWF) Library - shared library

``` 

Looking for any of these? No?

In that case, it's probably about your repositories:
[http://www.ubuntuguide.org/#flash-mozilla](http://www.ubuntuguide.org/#flash-mozilla)

---

