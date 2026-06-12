---
title: "Can not remove Synaptic Package Manager"
date: 2012-06-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Curtis6767 on 2012-06-13
I installed Synaptic last night hoping that it would assist in resolving some broken package problems that I got in trying to install Google Earth. Unfortunately, Synaptic was unable to locate and fix broken packages. 

I eventually fixed the problem by running: 

```
sudo apt-get f-install

sudo apt-get dist-upgrade
```I've had nothing but problems with Synaptic in my 12.04 install and had to remove it because anytime I tried to use it then my system wouldn't shut down until I pushed the power button. I removed it from 12.04 no problem. Now when I try to remove it from 12.10, I get the error below.

Maybe I should just leave well enough alone, but if there's a a way to remove Synaptic without borking my system, then I'd like to get rid of it. 

I have not tried any purge commands because I figure I'll just get the same error message.

Edit: I forgot to add that I'm running 12.10 in Virtual Box.

Edit # 2: Also, when I click on Remove All, that's when I get the error message. I'll try to add an image of that.

Edit # 3: Okay, sorry about this, but when I when I clicked on Remove All, this time it did it. I had shut down 12.10 in the interim and so whatever was causing the problem seems to have been resolved when I started 12.10. 

Thanks

---

### Post by jerrylamos on 2012-06-13
The first thing I do on installing Ubuntu is
sudo apt-get install synaptic
Then I set repository settings, add ubuntu partner, remove third party unknown, turn "update" as far off as I can, do refresh.
Then sudo aptitude update and sudo aptitude safe-upgrade (daily thereafter)
Use synaptic to install flashplugin-installer right away
Use synaptic to completely remove outdated linux-headers. 
Now I do use command line to remove outdated linux-image-whatever

Why am I concerned about getting rid of out of date never to be used files?  I usually have at least 4 partitions with various levels of Ubuntu unstable, stable, old ones that work 100%, plus library plus Windoze 7, ... so I don't want to have partitions any bigger than they comfortably want to be.

So I don't use synaptic a lot after that, except to find package names.  I recently used it to install "Opera" because recently "Ubuntu Firefox" won't do "AOL compose" but epiphany and opera will do AOL compose, as will Lucid Linux Firefox.

Oh, yes, on Lubuntu Quantal I use synaptic to remove completely Chromium which automatically installs Firefox.  I have a couple hundred bookmarks and have never been able to comfortably and easily handle bookmarks with Chromium.  Besides, Chromium takes more disk space.

Jerry

---

### Post by Curtis6767 on 2012-06-13
Jerry, thanks for all these tips and tricks.

---

### Post by kuvanito on 2012-09-01
sudo apt-get remove synaptic*
sudo apt-get purge synaptic*
sudo apt-get autoremove
sudo apt-get autoclean

the terminal is my best friend...

---

### Post by jerrylamos on 2012-09-01
BTW, synaptic hasn't been installed by default lately, I assume to save iso space for Unity expansion.  I either install synaptic when I have a need, or else get by with some cli:

sudo software-repositories-gtk
to turn ubuntu parners on and update manager off.  Development I do updates after checking the forum to see if update is causing problems today.

to try to guess the name of a package and what it is about.
apt-cache search <whatever>
apt-cache depends <whatever.
sudo apt-get install <whatever>
when dist-upgrade installs a new linux kernel reboot remove the last one:
sudo apt-get remove linux-image-3.5.0-12-generic
sudo apt-get remove linux-headers-3.5.0-12-generic
Synaptic is a lot of help and less likely to screw up especially on the last two.

Jerry

---

### Post by tartalo on 2012-09-01
> **jerrylamos said:**
> BTW, synaptic hasn't been installed by default lately, I assume to save iso space for Unity expansion.

Ubuntu Software Center replaced Synaptic, among other things to allow paid applications:

[http://www.thevarguy.com/2011/09/15/ubuntus-software-center-the-business-side-of-open-source/](http://www.thevarguy.com/2011/09/15/ubuntus-software-center-the-business-side-of-open-source/)

---

### Post by cariboo on 2012-09-01
> **jerrylamos said:**
> BTW, synaptic hasn't been installed by default lately, I assume to save iso space for Unity expansion.  I either install synaptic when I have a need, or else get by with some cli:

sudo software-repositories-gtk
to turn ubuntu parners on and update manager off.  Development I do updates after checking the forum to see if update is causing problems today.

to try to guess the name of a package and what it is about.
apt-cache search <whatever>
apt-cache depends <whatever.
sudo apt-get install <whatever>
when dist-upgrade installs a new linux kernel reboot remove the last one:
sudo apt-get remove linux-image-3.5.0-12-generic
sudo apt-get remove linux-headers-3.5.0-12-generic
Synaptic is a lot of help and less likely to screw up especially on the last two.

Jerry

Synaptic was removed from the default installation, as it was deemed to complicated for the target user, but you can do all the things jerrylamos suggested using synaptic.

---

