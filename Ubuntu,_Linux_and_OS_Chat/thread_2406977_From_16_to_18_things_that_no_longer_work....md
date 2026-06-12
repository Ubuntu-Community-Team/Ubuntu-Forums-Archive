---
title: "From 16 to 18: things that no longer work..."
date: 2018-11-28
forum: Ubuntu, Linux and OS Chat
---

### Post by uminkuphus on 2018-11-28
I've been a fairly happy user of Ubuntu, but since the move to 18, a number of things have broken.

I admit I'm venting a little after a month of tweaking my Ubuntu 18  installation. This is mostly a list of what  _doesn't work_. For those who, like me, keep googling up the same not-working solutions :D

I'm not looking for new suggestions; I work around the phone and scanner things by booting into Windows.

Copying photos from iPhone 4S to Ubuntu:
$:~ sudo apt-get install libimobiledevice-utils ifuse
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ifuse is already the newest version (1.1.3-0.1).
libimobiledevice-utils is already the newest version (1.2.1~git20180302.3a37a4e-1).
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
$:~ idevicepair unpair && idevicepair pair
ERROR: Device xxx is not paired with this host
$:~ sudo mkdir /var/lib/lockdown
mkdir: cannot create directory ‘/var/lib/lockdown’: File exists
$:~ sudo chmod 777 /var/lib/lockdown
$:~ idevicepair unpair && idevicepair pair
ERROR: Device xxx is not paired with this host

scanner Epson XP-235
Installed with
epson-inkjet-printer-escpr_1.6.5-1lsb3.2_amd64.deb
epson-printer-utility_1.0.0-1lsb3.2_amd64.deb
imagescan-bundle-ubuntu-16.04-1.1.10.x64.deb.tar.gz
from [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)
Simple Scan, Image Scan didn't work under Ubuntu 16.
Xsane did with the above installation under 16, but not under 18.
The first two crash at some point, Xsane fails to save the picture.

Mouse: set to lowest speed in Mouse & Touchpad preferences, I want it slower but can't.

Installed Tweaks. Now sometimes I get a wobbly sidebar that sometimes doesn't disappear when entering sleep mode, and then crashes the desktop.

Startup Applications Preferences: a bash script to slow the mouse and maker the screen less bright through Redshift, doesn't get run on startup like it would on 16.

---

### Post by QIII on 2018-11-28
Not a support request.  Moved to Ubuntu, Linux & OS Chat.

If you would like help with these issues, please start a separate thread for each in a support area of the Forums.  I suggest General Help, as Installations & Upgrades is for issues regarding those subjects specifically, not issues with the operation of the OS itself.

---

### Post by uminkuphus on 2018-11-28
Is OK with me. Where-ever my post lives, search engines will find it and hopefully sort it among the many instructions I found. Especially the iPhone one had that same suggestion mentioned a lot.

---

### Post by MoebusNet on 2018-11-28
I wonder if, in the interim, a Virtualbox guest installation of 16.04 would allow you to have everything working on host 18.04 until 18.04 gets up to speed? If worst comes to worst, I suppose you could replace 18.04 with 16.04 as host system (while it is still supported) with 18.04 as a VBox guest until 18.04 gets up to speed.

---

### Post by uminkuphus on 2018-11-28
Virtualbox with 16.04, that's a good idea, thanks! If just for connecting those couple of old devices.
I'll have to find some time for it - after a month of fixing things, it's time to put my computer to its actual use :-)

---

