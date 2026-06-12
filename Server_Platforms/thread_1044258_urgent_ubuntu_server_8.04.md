---
title: "urgent ubuntu server 8.04"
date: 2009-01-19
forum: Server Platforms
---

### Post by ash_dj on 2009-01-19
Hi all : 
this morning i tried a this commands to clean an ubunto server with ubuntu 8.04  ( and i think it was for ubuntu desktop non server ) 

sudo apt-get autoclean
ancellare gli archivi .deb dei pacchetti non più installati:

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get install deborphan
sudo apt-get remove --purge `deborphan`
sudo dpkg --purge `COLUMNS=300 dpkg -l "*" | egrep "^rc" | cut -d\ -f3` 

After last command it cancelled many packges and now the system wont boot , the fact is i istalled all with software raid1 and i need to save many important data on the hard disk   because i think i need to reinstall the server so how can i do it ? any help ? 

Thank you

---

### Post by .arean on 2009-01-19
You could try booting from a desktop live CD and access the data that way.

---

### Post by ash_dj on 2009-01-19
ii tryed , he don't let me in , i have raid in it

---

### Post by Joeb454 on 2009-01-19
Moved to Server Platforms

---

### Post by sunnydrake on 2009-02-08
hi i have too software raid(nvidia's) and by default, install do not support this type of setup...
i used dmraid tool (use apt-get,it support many raid systems ):) 
with correct setup of this tool you can gain access to raided partitions via linux LiveCD/OS on Flash if your software raid supported by it(or find tool that can handle your raid).
if you wish to reinstall os with this raid(i'm not a pro in this type of work) you can try my way: make flash ubuntu liveCD/install boot from it, apt-get dmraid (or tool of your choice) setup it, run GUI system installer, chroot to installed system then modify grub loader options to support raid boot.
There is a doc i found it somewhere here by keywords "howto install dmraid ubuntu".

---

### Post by jimv on 2009-02-08
In the future, there's really not any reason to run anything other than these two when cleaning up old packages:

sudo apt-get clean <-- gets rid of downloaded packages
sudo apt-get autoremove  <-- removes dependencies that that have nothing depending on them anymore.

Anything else risks removing things that should not be removed.

---

