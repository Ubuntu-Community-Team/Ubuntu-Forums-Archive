---
title: "Updating Firefox flash plugin"
date: 2013-08-16
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2013-08-16
I previously installed the Firefox flash plugin via the Ubuntu software centre. It is now out of date. There is no update via the software centre. So I have downloaded the install_flash_player_11_linux.x86_64 file.

Could someone please give me the exact path to copy the libflashplayer.so file in Ubuntu Studio 12.04?

---

### Post by GwL3eNC on 2013-08-16
Hello,

ist this a tar gz file, a deb file or which ending?

sudo cp libflashplayer.so /usr/lib/flash-plugin/

---

### Post by shaunthesheep on 2013-08-17
It is a tar gz file which I have extracted to a folder on my desktop. Running 
sudo cp libflashplayer.so /usr/lib/flash-plugin/ results in message "cp: cannot stat `libflashplayer.so': No such file or directory"

In fact I don't seem to have much luck running any commands in the terminal emulator. They all seem to fail for some reason or other. Is Ubuntu locked down in some way?

---

### Post by jejeman on 2013-08-17
I guess you are not using guest user, so terminal is not "locked", you need to know what you are doing, learn it etc.
Is your working directory set where the libflashplayer.so file is? and so on..

---

### Post by Frogs Hair on 2013-08-24
Adobe is no longer developing Flash for Linux which means the current version will only receive security updates . This is why the Windows version is different . Google provides Pepper Flash with the Chrome browser , So far the version in the software center has proven reliable on all the sites I visit.  

[http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux](http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux)

---

### Post by Yellow Pasque on 2013-08-25
This is the latest Mozilla plugin version for Linux: [https://launchpad.net/ubuntu/+source/flashplugin-nonfree/11.2.202.297ubuntu0.12.04.1](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/11.2.202.297ubuntu0.12.04.1)

> sudo cp libflashplayer.so /usr/lib/flash-plugin/ 
It's a bad idea just to dump files not belonging to a .deb into /usr/lib
If, for some reason, one needs to install libflashplayer.so, it would be better off in the ~/.mozilla/plugins or maybe /usr/local/lib in a multiuser setup.

---

### Post by bcschmerker on 2013-08-28
> **Frogs Hair said:**
> Adobe is no longer developing Flash for Linux which means the current version will only receive security updates . This is why the Windows version is different . Google provides Pepper Flash with the Chrome browser , So far the version in the software center has proven reliable on all the sites I visit.  

[http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux](http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux)
Excellent point.  I'm currently testing Chromium™ 28.0.1500.71 (package: chromium-browser) and Pepperflash™ 11.8.800.115 (package: pepflashplayer-installer; requires PPA:skunk/pepper-flash) alongside the stock Mozilla® Firefox® 23.0 and Adobe® Flash Player® 11.2.202.297 (packages: firefox, adobe-flashplugin), and an ongoing test I am conducting on [SingSnap®](http://www.singsnap.com/) gives Chromium™ the advantage for certain multimedia-heavy Websites in need of later Adobe® Flash™ versions.  (YouTube™, now a Google® service, has shown itself compatible with all subreleases of Flash Player® 11.x.)

---

