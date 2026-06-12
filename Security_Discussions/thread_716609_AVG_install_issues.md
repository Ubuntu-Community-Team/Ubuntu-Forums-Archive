---
title: "AVG install issues"
date: 2008-03-06
forum: Security Discussions
---

### Post by prasad_bhatla on 2008-03-06
Hi

On Ubuntu 7.06 with all upgrades, I tried to upgrade AVG and get the following error:
E: avg75fld: subprocess pre-removal script returned error exit status 150

bhatla@home-desktop:~$ sudo dpkg -i media/usbdisk/avg75fld-r49-a1130.i386.deb

Password:(Reading database ... 127274 files and directories currently installed.)
Preparing to replace avg75fld 7.5.45_a0973 (using .../avg75fld-r49-a1130.i386.deb) ...
 * Stopping avgdkill: 246: Illegal number: -local: 246: 3949: bad variable name( not running)
*[fail]invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 150
dpkg - trying script from the new package instead ... 
* Stopping avgdkill: 246: Illegal number: -local: 246: 3949: bad variable name( not running) *  

I would like to remove all instances of AVG and make a fresh start.

( Incidentally, I use AVG ae files are ported between windoze machines).

How to delete/remove AVG completely ??

Cheers

bhatla

---

### Post by mikewhatever on 2008-03-07
<sudo dpkg -P -R avg75fld>. P stands for purge and R for recursively.

> How to delete/remove AVG completely ??

You might want to think of a different thread title, because removing AVG is not the same as installing it.

---

### Post by prasad_bhatla on 2008-03-07
Hi

 Problem solved. I followed a method listed in the AVG Linux forum:

Stopped the daemons, --- kill the daemons and remove their
lockfile by running commands

$ sudo killall avgscan
$ sudo rm /var/lock/avgd

Then did an install  by  dpkg . The old version was replaced.

Thanks for the response.

Cheers

Bhatla
:)

---

