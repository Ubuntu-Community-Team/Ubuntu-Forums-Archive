---
title: "Ubuntu 8.10 on HP Proliant DL320 G5"
date: 2008-10-31
forum: Server Platforms
---

### Post by dravidan on 2008-10-31
The installation completes fine with serial ATA RAID devices activated but when booting it drops to shell.  This is what I see when I boot:

******************************
Starting up ...
Loading, please wait...
[     2.930100] hub 3-0:1.0: unable to enumerate USB device on port 2
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enought?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/ddf1_R11 does not exist. Dropping to a shell!

BusyBox v1......
Enter 'help' ......

(initramfs) 

*******************************

Is it possible to install Ubuntu in this server or should I give up and use Debian etch?

---

### Post by cariboo on 2008-10-31
How did you set up your raid array? Is it an add on card or is the raid onboard the motherboard?

Jim

---

### Post by dravidan on 2008-10-31
It an onboard RAID

---

### Post by ^[H3ad-Tr1p]^ on 2008-11-01
hi have the same problem

how did you have solved?

---

### Post by dravidan on 2008-11-01
Never resolved, I ended up going with 8.04 version of Ubuntu.
Here is the link to set it up in 8.04: [http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

---

### Post by lptr on 2008-12-22
What type do you use? Manufacturer number 445433-421 ? Is this with Intel Xeon on board chipset                                                                        Intel 3210 and ethernet controller                                                                        HP NC326i ?

Can you tell me, if SATA ctrlr can be set as normal 4 channel SATA controller not using any fakeRAID etc.?

Thanks

rob*

---

### Post by dravidan on 2008-12-22
It is with Intel Xeon 3050.  I think I am using fakeRAID but see the above link for more info.

---

### Post by lptr on 2008-12-22
dravidan: Thanks for your fast reply.

My question was - if it is possible to switch it to normal SATA mode. For example for using just one single harddisk drive.

If you having tech docs of this machine handy, would you mind please having a look into it - for me? I would highly appreciate that. Even intensive researching the Internet to finding that manuals myself did not lead to any success, yet :(


rob*

---

### Post by vortmax on 2008-12-22
> **lptr said:**
> dravidan: Thanks for your fast reply.

My question was - if it is possible to switch it to normal SATA mode. For example for using just one single harddisk drive.

If you having tech docs of this machine handy, would you mind please having a look into it - for me? I would highly appreciate that. Even intensive researching the Internet to finding that manuals myself did not lead to any success, yet :(


rob*

I hit this same problem on the G-4's.  Maybe the G5 is different, I don't know.  I could not bypass the raid controller.  The bios would boot using the configured raid array, then the OS would just seen individual drives.

To bypass it, I just set up 2 raid0 arrays (one per drive).  There is still a software layer involved, but it makes the boot process and the OS agree on drive layout.  I tried to build a software fakeraid on top of that, but it was really slow, so I gave up on it.

Now...I have an old G2 who's raid controller is recognized by linux and I'm running full bios level software raid1.

---

### Post by lptr on 2008-12-22
Anyone knows the difference between DL320 G5 and DL320 G5p ?

rob*

---

### Post by lptr on 2009-01-11
Ok. Just for those who are interested in:

We recently bought into a HP Proliant DL360 G5. 

Hardy 8.04.1 64 Bit server is running there on a mirror (RAID1+0) that is controlled by a P400i Smart Array Controller.

All is working very smoothly. Installation worked without any hitches.

I did some testings with Intrepid server (both versions 32 Bit and 64 Bit) before we decided to take the Hardy LTS version. Intrepid installed and ran ok, too.  

Q: Anybody tried the system specific drivers/apps from HP for this box running under Ubuntu? [FONT=Arial][SIZE=2][HP        System Health Application]("http://h20293.www2.hp.com/portal/swdepot/displayProductInfo.do?productNumber=T8569AAE") and Insight Management Agents and the like?[/SIZE][/FONT] What are the experiences?


rob*

---

