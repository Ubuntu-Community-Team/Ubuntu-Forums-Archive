---
title: "install 8.04.1 on IBM x3850"
date: 2008-07-29
forum: Server Platforms
---

### Post by skubij on 2008-07-29
Ubuntu 8.04.1 can not be installed on this platform.
After choosing the language, progress reaches 100% and stops after which it hangs

Installation is impossible

Server IBM x3850, 
4 x Xeon Quad Core X7350,
32 G RAM

Does anyone tried to install this equipment?

---

### Post by kevala on 2008-09-27
I am experiencing the same problem trying to install 8.04 on an IBM System x3400.

Does anybody have any idea how to make this work?

---

### Post by adrianmoisey on 2008-09-27
any news on Hardy on the x3850?  I'm also having issues with it and would like to get it running on that IBM machine

---

### Post by skubij on 2008-09-27
Hi.
The problem turned out to be simple.
The installer was not able to identify 16 processors! It took a leave, 4 cored and installation went.
Then recompile kernel and enable more processors and memory BIG_MEM.
Then usually make-kpkg and walking.
Of course, to connect the network (Broadcom is invisible) insert the network card supported by ubuntu/Debian

---

### Post by whocarez on 2008-10-09
Thanks for some useful hints. I've been struggling with installing Debian/Ubuntu on this server myself. Both Ubuntu and Debian Etchnhalf would hang on boot. My configuration has only 8 cores though. The solution for me was to install Debian Etch amd64 ( kernel 2.6.18 ), which boots fine, and then compile the Broadcom Netxtreme II (ver. 1.7.6b at this time) driver I found here:
[https://www-304.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=MIGR-5070029&brandind=5000008](https://www-304.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=MIGR-5070029&brandind=5000008)

The .tgz-file has the source code and is very easy to compile once you get the kernel header-files and build-essential packages. I do have some timing issues with this driver sometimes, looks like it doesn't always manage to bring the link up right during boot, even if I add a delay. It usually works fine right after boot. I'm not sure if it is driver-related or not, need to try with more network equipment and a newer kernel.

I'll certainly try a kernel with support for more cpus and BIG_MEM support.

---

### Post by adrianmoisey on 2008-10-20
Has anybody managed to get hardy running on this with 16 CPUs ?
I've managed to boot with 1 CPU, but what must I change to make it boot with 16 CPUs?

---

### Post by rlach on 2009-04-24
> **skubij said:**
> Hi.
The problem turned out to be simple.
The installer was not able to identify 16 processors! It took a leave, 4 cored and installation went.


What do you mean by above? How did you install it?

R.

---

