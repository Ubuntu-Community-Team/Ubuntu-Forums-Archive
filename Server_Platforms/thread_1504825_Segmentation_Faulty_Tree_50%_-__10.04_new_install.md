---
title: "Segmentation Faulty Tree 50% -  10.04 new install"
date: 2010-06-08
forum: Server Platforms
---

### Post by ZenMasta on 2010-06-08
I searched the forums for this but only found an old topic suggesting to
rm -vf /var/cache/apt/*.bin

This does not work
I've tried with aptitude and apt-get Sometimes it has said
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
But that does not correct the problem. 

This is a clean install (no upgrade or dual boot), the only changes I have made have been to install openssh and set a static ip/hostname :confused:
Additionally, I've aldo tried:
> zenmasta@wombocombo:~$ sudo ubuntu-bug aptitude
[sudo] password for zenmasta:

*** Collecting problem information

The collected information can be sent to the developers to improve the
application. This might take a few minutes.
Segmentation fault

---

### Post by camdude on 2010-07-20
Try running this command in the terminal:
'sudo rm -vf /var/cache/apt/*.bin' (without quotes)

---

