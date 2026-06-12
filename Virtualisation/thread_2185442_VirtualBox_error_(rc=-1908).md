---
title: "VirtualBox error (rc=-1908)"
date: 2013-11-02
forum: Virtualisation
---

### Post by lewisjroutledge on 2013-11-02
Hello All, 

I'm fairly new to Ubuntu so first of all I'm sorry if I seem pretty noob! I've installed VirtualBox using Ubuntu Software Centre, however when I try and start a virtual machine I get the below error;

 [SIZE=1][I]The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/I][/SIZE]

I have ran some commands below which I'm hoping will give you guys some clarity on what is on my machine and will help me fix this :D!

Also I have tried removing and reinstalling Virtualbox, however to no avail it did not fix my problem. 

shingdayho@shingdayho:~$ ls /etc/init.d/v*
/etc/init.d/virtualbox              /etc/init.d/virtualbox-guest-x11
/etc/init.d/virtualbox-guest-utils

shingdayho@shingdayho:~$ uname -a
Linux shingdayho 3.5.0-42-generic #65-Ubuntu SMP Tue Oct 1 23:38:22 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

shingdayho@shingdayho:/$ ls /usr/src/
linux-headers-3.5.0-17  virtualbox-4.1.18  virtualbox-guest-4.1.18

shingdayho@shingdayho:/usr/src/virtualbox-4.1.18$ ls
common     generic  Makefile  r0drv  vboxdrv     vboxnetflt
dkms.conf  include  math      VBox   vboxnetadp  vboxpci

shingdayho@shingdayho:/usr/src/virtualbox-4.1.18/vboxdrv$ make
Makefile:184: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

Thankyou for taking the time to look into my problem :)!

---

### Post by bashiergui on 2013-11-23
Download and install the newest verson ov virtualbox from the oracle website. Should fix it.

---

### Post by lewisjroutledge on 2014-01-26
Yup. That fixed it, thanks a lot dude :)

---

### Post by free_bird573 on 2014-01-27
I'm getting the same error.  

OS:  Linux 12.10
Virtual Box:  4.3.6-91406
5 G of Ram
XP SP3 is what I'm trying to run

I have tried 4.2.20 and I get the same error.

Didn't have this issue on 12.04, but I wanted to run 12.10, 'cause it is newer

---

