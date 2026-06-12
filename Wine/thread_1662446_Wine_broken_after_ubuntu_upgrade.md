---
title: "Wine broken after ubuntu upgrade"
date: 2011-01-08
forum: Wine
---

### Post by Kg001 on 2011-01-08
I recently upgraded Ubuntu 9.04 64 bit to to 10.04 (via 9.10) Everything works with only a couple of minor hiccups that were easily sorted, except that wine was uninstalled at some stage of the upgrade process & now flat refuses to reinstall I have renamed the .wine directory Tried every thing I can think of including 1.0 1.2 & version 1.3 all to no avail These are the error messages I get in the terminal

-----------------------------------------------------

nevilleb@nevilleb-desktop2:~$ sudo apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine1.3: Depends: ia32-libs (>= 1.6) but it is not going to be installed
           Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
           Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
           Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
E: Broken packages

----------------------------------------------------------

any help will be appreciated note a clean install of Ubuntu is not a real option as there is just too much invested in the current setup & with 9.04 no longer supported I am not keen to restore the backups & revert

---

### Post by dino99 on 2011-01-08
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by YokoZar on 2011-01-08
> **dino99 said:**
> [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

No.

Please try removing some packages:

sudo apt-get remove wine wine1.2 wine-dev wine1.2-dev wine1.3 wine1.3-dev
sudo apt-get -f install

Then:

sudo apt-get install wine1.3


Did you have a PPA version of Wine when you had 9.04 installed by chance?  I have a feeling you have a very old "wine" package there conflicting with things.

---

### Post by Kg001 on 2011-01-14
Thanks for the tips however it Didn't work I'm afraid, the terminal output is below. 

---------------------------------------
nevilleb@nevilleb-desktop2:~$ sudo apt-get remove wine wine1.2 wine-dev wine1.2-dev wine1.3 wine1.3-dev
[sudo] password for nevilleb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
Package wine1.2 is not installed, so not removed
Package wine-dev is not installed, so not removed
Package wine1.2-dev is not installed, so not removed
Package wine1.3 is not installed, so not removed
Package wine1.3-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
nevilleb@nevilleb-desktop2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
nevilleb@nevilleb-desktop2:~$ sudo apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine1.3: Depends: ia32-libs (>= 1.6) but it is not going to be installed
           Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
           Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
           Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
E: Broken packages
-------------------------------------------------------
This machine has been up now constantly for a couple of years last major rebuild was just after the release of 9.04 so the installed version of wine would have dated from that time. The interesting bit is that I have also had the first serious crash ever, that left me with a bunch of orphaned inodes this afternoon Current hardware is a phenom2 x6 in a gigabyte am2+ board with 4g ram. There is a copy of XP running under virtual box 24/7 with a SCADA application scanning & logging a bunch of modbus serial devices hence the reluctance to do a clean rebuild. Im not a total Linux newbie but no geek either so forgive me if this question is stupid, but is it possible that there is a corrupted wine package on my local machine that gets in the road?

---

### Post by Kg001 on 2011-01-14
A further update 
The comment about old packages set me thinking so I went into software sources & removed anything with a mention of wine, I can now install wine 1.2 via the Ubuntu software center but still can't get 1.3 to install 
----------------------------------
E: Couldn't find package wine1.3
---------------------------------

Back to reading forums thanks for the help guys.

---

### Post by cogadh on 2011-01-14
Instructions for installing Wine 1.3.X:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Kg001 on 2011-01-15
Thanks for the help. Wine 1.3 is up & running & several things I have never been able to run now work!

---

