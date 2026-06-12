---
title: "Trouble with raid5 after upgrading to 8.04"
date: 2008-05-15
forum: Server Platforms
---

### Post by Terrasque on 2008-05-15
I'm experiencing some problems with my raid5 array after upgrading from ubuntu 6.06 to 8.04.

If I transfer large amounts of data to it (for example over FTP or SMB) it stops working properly. Small writes still work, but I suspect they're just being cached. A sync hangs, and can't abort it with ctrl-c. The load creeps up slowly, and usually stops around 30-40. Writes to system disk (80gb sata on a different controller) seem to also be affected.

Most of the time I don't see anything in dmesg, top, ps x or /var/log/messages. I have tried to upgrade kernel to 2.6.24-17-server, as that fixed a similar issue for one at IRC, but still the same.

Basic info:
 raid5 array, 3tb, 7 hdd's
 Server is 64bit, upgraded from 6.06 to 8.04
 XFS filesystem
 SATA cards are 2x : Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)
 
This worked perfectly in 6.06 server. Upgrade was done via the do-release-upgrade tool.

I have on two occations seen page allocation failures in dmesg following these problems, but I think those are symptoms and not the cause.
[ 1721.538312] swapper: page allocation failure. order:1, mode:0x4020
[ 1721.538320] Pid: 0, comm: swapper Not tainted 2.6.24-17-server #1

As far as I can tell, the problem lies in the kernel, but I'm unsure of where. It can be the XFS filesystem, the raid system, or the basic disk I/O. The kernel is tight lipped as to where it happens.. Anyone got any ideas?

---

### Post by Terrasque on 2008-05-16
Just an update, I've worked around the problem by using the old 6.06 kernel (2.6.15-51-amd64-server). But that is not an ideal solution..

---

### Post by Terrasque on 2008-07-31
A bump on this one.. Same problem with the 2.6.24-19-server kernel. But it seems like it takes longer time to happen, and load is much lower, currently at around 9.

I still have no idea as to the cause of it, but the old dapper kernel (2.6.15-51) still works..

Anyone have any good idea?

---

### Post by Pieter1974 on 2009-01-09
This problem seems to be fixed with updating to 

linux-image-2.6.24-23

It's rolled out now on all our servers and the problem seems to be disappeared

Just use apt-get dist-upgrade.

---

### Post by Cracauer on 2009-01-09
Scary.

Were you using Linux' md driver or the SATA raid junk?

---

### Post by Terrasque on 2009-01-10
Yes, I am using the Linux md driver. 

I eventually solved the problem by compiling the latest linux kernel by hand (2.6.26.2-custom). As a bonus, I got a nice performance increase in read / write speed.

As everything is working perfectly now, I'm hesistant to make any changes to the setup.

---

### Post by Cracauer on 2009-01-10
> **Terrasque said:**
> Yes, I am using the Linux md driver. 

I eventually solved the problem by compiling the latest linux kernel by hand (2.6.26.2-custom). As a bonus, I got a nice performance increase in read / write speed.

As everything is working perfectly now, I'm hesistant to make any changes to the setup.

Still scary.

I have been running Linux md constantly for many years now, on many machines. I always upgrade to "random" kernels and never had any problem with md and my existing arrays.

I never, ever, use distribution-provided kernels (Ubuntu, Redhat etc.), though.

---

### Post by fjgaude on 2009-01-10
> **Cracauer said:**
> Still scary.

I have been running Linux md constantly for many years now, on many machines. I always upgrade to "random" kernels and never had any problem with md and my existing arrays.

I never, ever, use distribution-provided kernels (Ubuntu, Redhat etc.), though.

The same has gone for me since about 6.04... one thing I do usually is let the kernel and its **md** create the **mdadm.conf** file automatically when transferring an array from one machine to another. I never used an old file that was on another machine!

And I always have triple backups: one online, one near-line, and one off-line.

---

