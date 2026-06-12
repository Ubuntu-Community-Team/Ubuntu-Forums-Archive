---
title: "Can't get rid of TrueCrypt 5.1a to install ver. 6.0"
date: 2008-10-04
forum: Security
---

### Post by Marc Ament on 2008-10-04
As I'm trying to upgrade to TrueCrypt ver. 6.0, I can't get rid of version  5.1a. Ver. 5.1a doesn't show up on Synaptic, but it opens with Run Application and at the terminal.  However, when I run apt-get remove, I get the message 

root@marc-laptop:~# apt-get remove truecrypt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package truecrypt is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

A file search shows TrueCrypt in /usr/local/bin.  I've tried changing directories to that before running apt-get, with same negative results.

Dell 1420 Hardy.  Thanks.

---

### Post by tigerstripedcat on 2008-10-04
Try installing the old version then:

sudo apt-get remove truecrypt --purge

Every directory that says "could not remove this directory because there are files..." then remove files/directories carefully.  Apt-get won't purge directories/files that have been changed

you could do:
sudo updatedb
locate crypt -i
then just rm -rf any files that linger

TSC

---

### Post by Marc Ament on 2008-10-04
Thanks, tsc: 
Your second suggestion worked for me, though for "locate" I had to use "truecrypt" instead of "crypt" (which brought up too much other stuff that clearly needed to stay there):

sudo updatedb
locate truecrypt -1
rm -rf [any remaining files]

I then tested for version 5.1a, and it was now gone as I wanted it to be.  I installed version 6.0a-0, and it works perfectly (and is now accessible through Run Application as well as at the terminal).

---

