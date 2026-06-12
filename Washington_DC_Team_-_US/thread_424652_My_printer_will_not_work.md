---
title: "My printer will not work"
date: 2007-04-26
forum: Washington DC Team - US
---

### Post by andreasM on 2007-04-26
I have added Ubuntu to my WinXP computer, hoping to eliminate WinXP once Ubuntu gets going. My new printer/scanner/copier, Brother MFC-665CW will not work with Ubuntu. I have tried using the drvers for printers MFC-6550MC, and MFC-7150C without success. My knowledge of Ubuntu is minimal. Will appreciate any explicit help!

---

### Post by KevinCole on 2007-04-28
It appears this has been answered in:

[COLOR="Blue"][B][URL="http://ubuntuforums.org/showthread.php?t=301112"]http://ubuntuforums.org/showthread.php?t=301112
[/URL][/B][/COLOR]
However, I don't know if the answer there is explicit enough for you, since you say you're a beginner.  So... At the bottom of the post there are two attached files for you to download.  These are Debian packages, which you can think of as zip files with delusions of grandeur. ;-)  These are files that contain both files needed for a particular package, and also scripts that handle the proper installation, plus information describing the package, including the version number.  Programs like [COLOR="DarkRed"]synaptic[/COLOR], [COLOR="DarkRed"]adept[/COLOR], [COLOR="DarkRed"]apt-get[/COLOR], [COLOR="DarkRed"]aptitude[/COLOR] and [COLOR="DarkRed"]dpkg[/COLOR] allow you to install, remove, upgrade, or get detailed information on particular packages.

So, download the two files attached to that post.  (I will assume they download to your desktop.) Then, open a terminal window (a.k.a. console window), and type:
```
cd Desktop/
sudo dpkg -i mfc665cwcupswrapper-1.0.0-6.i386.deb mfc665cwlpr-1.0.0-6.i386.deb
```
Supply your password when asked for it, and wait.  When it finishes, type "exit" and then try experimenting with your printer.  (You will probably need to go to your printer configuration and install a new printer, but now your Brother should show up in the list.)

---

### Post by macogw on 2007-04-29
You don't even need that bit of code.  Double click on the files and GDebi will start up and have an "install package" button.  Use that.

---

