---
title: "Ethernet (e1000e) has-to-be-activated  bug"
date: 2013-02-20
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-02-20
Hi,

I reported this bug :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652)

The ethernet connection (e1000e driver) is only working when I do what is written in this bug report.

Does anyone experience the same bug ?

Thx !

---

### Post by ft_ on 2013-02-21
hope from the huge changes in :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2013-02-21-raring/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2013-02-21-raring/CHANGES)

---

### Post by ft_ on 2013-02-22
when I plug in ethernet before booting, ethernet is on and fully functional. When I plug the cable after boot, I have to enter the above workaround.

What is the file which tells the system to awake eth0 when hot-plugged in ?

---

### Post by dino99 on 2013-02-22
a report has already been posted on launchpad, describing quite the same issue as yours

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018561](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018561)

but sadly there is not much updates since the date report. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018561](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018561)

and you seems not alone complaining about e1000e
[http://ubuntuforums.org/tags.php?tag=e1000e](http://ubuntuforums.org/tags.php?tag=e1000e)

---

### Post by ft_ on 2013-02-22
Well, I do not find the bug you quote to be nearly the same as mine ?
I tried the daily ubuntu kernel but nor progress. Maybe is it an upgrade (from Quantal) issue ? But ethernet used to work fine until 3.8.0-1 ubuntu kernel.

---

### Post by ft_ on 2013-02-22
There's something wrong, I do not know if it is related : when I turn off the wifi switch of my laptop, the wifi icon remains activated. The same behaviour happens with ethernet (when activated).

Could it be a network-manager issue ? When we were dealing with the first 3.8 raring kernels, switching back to 3.8.0-1 allowed me to get a normal behaviour of ethernet port. So I think it's kernel-related. Am I wrong ?

---

### Post by dino99 on 2013-02-22
you still could install wicd and purge networkmanager to see if that makes difference

---

