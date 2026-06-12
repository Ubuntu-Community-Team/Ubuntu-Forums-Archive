---
title: "Multiple status: { DRDY ERR } errors"
date: 2010-07-30
forum: Server Platforms
---

### Post by Zeophlite on 2010-07-30
So I have a server at home running Lucid, and it stopped serving a few weeks ago.  I couldn't SSH or web to it.  I believe that there was a powersurge or a roommate accidentally unplugged it.  As I couldn't access it, I held down the power button until it shutdown, then unplugged it and moved it to my TV so I could try and fix it.  When I booted, it had this error:

```


fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/mapper/Mustrum-root contains a file system with errors, check forced.
/dev/sda1: clean, 204/124496 files, 35686/248832 blocks
/dev/mapper/Mustrum-root: Inodes that were part of a corrupted orphan linked list found.

/dev/mapper/Mustrum-root: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
mountall: fsck / [356] terminated with status 4
mountall: Filesystem has errors: /

```

But eventually got to the login screen. I ran
fsck /dev/sda1
which seemed to fix that - when I restarted it, I think it gave something like:
```

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 204/124496 files, 35686/248832 blocks

```
or something similar

However now when I start up or shut down, it gives lots of these blocks of information:
```

[  xxx.xxxxxx] ata1.00: status: { DRDY ERR }
[  xxx.xxxxxx] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  xxx.xxxxxx] ata1.00: irq_stat 0x40000001
[  xxx.xxxxxx] ata1.00: failed command: READ DMA EXT
[  xxx.xxxxxx] ata1.00: cmd 25/00:08:f0:bf:4b/00:00:20:00:00/e0 tag 0 dma 4096
[  xxx.xxxxxx] ata1.00: res 51/01:00:f0:bf:4b/00:00:20:00:00/e0 Emask 0x1 (device error)

```
with the x's increasing each line

followed by a
end_request: I/O error, dev sda, sector 541835248
after startup.


The machine is plugged into my TV via HDMI right now, and so I turned the screen off whilst I wrote this.  When I came back it had more of these error messages.  All the error codes appear to be the same.

I tried to do a
e2fsck -f -c -v /dev/sda1
but it didn't help.

I also tried to boot off a recovery CD:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
but it didn't boot off of it.


I can access all my files normally, and it appears that everything from my server is running (as it gives Apache stopping 
 messages when I tell it to shutdown).

How can I fix this, and how can I prevent this from happening again?  Can't it try and fix itself when it boots up after a unclean shutdown?

Thanks for your help

---

### Post by Zeophlite on 2010-07-30
I can boot it into "Recover broken system" from my install cd, but I'm unsure what to do.

I also just noticed I'm also getting "failed command: READ FPDMA QUEUED" errors as well

---

### Post by Zeophlite on 2010-08-01
Is it somehow possible to find out what's causing these messages to appear?
What logs should I look in/post?

I really don't want to just reinstall Lucid, as this error may just continue, or happen again.

---

### Post by FuturePilot on 2010-08-01
> But eventually got to the login screen. I ran
fsck /dev/sda1
Did you run fsck on a mounted partition?

---

### Post by Zeophlite on 2010-08-01
I guess I did.  It did give a warning, but I ignored it, as I din't know how else.  Did that cause the DRDY ERR messages?  If this happened again, how else could've I run fsck?  I only have the one hard drive.  Just boot in recovery mode off the install CD, then run from there?  I'm pretty sure it still had the same message.  What can I do to fix it now?

---

### Post by FuturePilot on 2010-08-01
> **Zeophlite said:**
> I guess I did.  It did give a warning, but I ignored it, as I din't know how else.  Did that cause the DRDY ERR messages?  If this happened again, how else could've I run fsck?  I only have the one hard drive.  Just boot in recovery mode off the install CD, then run from there?  I'm pretty sure it still had the same message.  What can I do to fix it now?

Boot the live CD and run fsck from there.

---

### Post by Zeophlite on 2010-08-02
Okay I put in the Ubuntu Server 10.4 Install CD, and choose Rescue a Broken System, then:

Device to use as root file system:
	/dev/sda1
	/dev/sda2
	/dev/sda5
	/dev/Mustrum/root
	/dev/Mustrum/swap_1
[x]	Do not use a root file system

Rescue Operations
[x]	Execute a shell in the installer environment
	Choose a different root file system
	Reboot the system

~ # fsck
/bin/sh: fsck: not found

So what should I do now?

Also next time I have a power failure, how can I get it to fix itself automatically?  I couldn't SSH into my server, and this lugging out monitors and keyboards is a pain.

---

### Post by Zeophlite on 2010-08-02
I also tried

e2fsck -d -c -c -v -f /dev/sda1

then rebooting, but I keep getting the ata1.00 errors

---

### Post by FuturePilot on 2010-08-02
Do you have the desktop live CD? The server edition is just an installer and it doesn't have a lot of tools available as you can see (no fsck).

> Also next time I have a power failure, how can I get it to fix itself automatically? I couldn't SSH into my server, and this lugging out monitors and keyboards is a pain. 

If you can't connect to it there's really no other option.

---

### Post by Zeophlite on 2010-08-02
From ubuntu live CD:

```

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: clean, 204/124496 files, 35686/248832 blocks

```

Reboot still has same ata1.00 errors

---

### Post by FuturePilot on 2010-08-02
Hmmm. Well it doesn't appear to be file system corruption. If there was in fact a power surge then I would start suspecting a hardware problem. Perhaps try unplugging and replugging everything inside the server. Sometimes that has some magical effect.

---

### Post by Zeophlite on 2010-08-03
Okay so now I tried using smartmontools - I'm trying to follow  [http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)
```

**sudo smartctl -t short /dev/sda1**
...
**sudo smartctl -l selftest /dev/sda1**
...
Num	Test_Description	Status				Remaining	LifeTime(hours)		LBA_of_first_error
# 1	Short offline		Completed: read failure		90%		317			541835248
**sudo fdisk -lu /dev/sda1**

Disk /dev/sda1: 254 MB, 254803968 bytes
255 heads, 63 sectors/track, 30 cylinders, total 497664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk Identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table

```

I note that the LBA_of_first_error matches this line:
end_request: I/O error, dev sda, sector 541835248

Now when I try this though:
```

**sudo fdisk -lu /dev/sda**

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk Identifier: 0x00051561

   Device	Boot	Start		End		Blocks		Id	System
/dev/sda1	*	2048		499711		248832		83	Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2		501758		625141759	312320001	5	Extended
/dev/sda5		501760		625141759	312320000	8e	Linux LVM

```

Now I'm unsure what to do to resolve my problem.

---

### Post by stlsaint on 2010-08-03
I just had a laptop running windows give those same errors at my job and it turned out to be a bad harddrive. I suggest backing up all your data ASAP and then try fixing drive maybe with something like hirens boot disc. In my situation the drive was literally unreadable so i had am in the process of trying out forensics on the drive.

---

### Post by Zeophlite on 2010-08-08
Well I can still access all my data, so I doubt that its a broken hard drive - the hard drive is a high quality one, and its only several months old.

Unplugging everything did not have the desired magical effect.

I posted a Bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/613880](https://bugs.launchpad.net/ubuntu/+bug/613880)

It has several log files.

---

### Post by ian dobson on 2010-08-08
Hi,

Have you tried replacing your wiring? I was getting  { DRDY ERR } errors from my RAID5 array until I replaced all the sata cables.

Regards
Ian Dobson

---

