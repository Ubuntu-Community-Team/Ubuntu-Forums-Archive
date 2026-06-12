---
title: "No GRUB after 10.10 install in RAID"
date: 2011-01-04
forum: Server Platforms
---

### Post by ztrange on 2011-01-04
Hi,

I'm installing Ubuntu 10.10 Server 64 bits on a Dell Poweredge SC440 box running an Intel Xeon and a two drive RAID.

I installed the core system with a live USB and when I rebooted, the computer got forzen after "starting the SAS utility" (I think is something for the RAID). Well, I restarted it using my USB drive and I could boot the system; everything looks fine.

But now I think I have no grub and I really don't know where to go from here. I've never faced this kind of problem before.

If i run sudo grub-install /dev/sda1 I get:
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.

But I really don't know how to deal with RAID drives. 
Can anybody point me in the right direction?

Thanks in advance.

---

### Post by truant on 2011-01-05
This sounds an awful lot like the problem I'm having with my Dell Poweredge R310.  

[edit: I think my problem is different.  I'll leave this thread to you, ztrange, my problem is now posted here: [http://ubuntuforums.org/showthread.php?p=10319667](http://ubuntuforums.org/showthread.php?p=10319667) ]

---

### Post by truant on 2011-01-05
> **ztrange said:**
> Hi,
If i run sudo grub-install /dev/sda1 I get:
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.

But I really don't know how to deal with RAID drives. 
Can anybody point me in the right direction?

OK, a few questions:

1. hardware raid or software?

2. do you have a non-raid /boot partition?  Grub doesn't like booting from a software raid device.

3. what happens if you do "grub-install /dev/sda" to install to the MBR rather than to a partition?

---

### Post by psusi on 2011-01-05
> **truant said:**
> 
2. do you have a non-raid /boot partition?  Grub doesn't like booting from a software raid device.


Grub2 handles this fine.

Posting the output of fdisk -lu, or the bootinfo script would be helpful.

---

### Post by truant on 2011-01-05
> **psusi said:**
> Grub2 handles this fine.

Posting the output of fdisk -lu, or the bootinfo script would be helpful.

From what I've read, not with RAID metadata levels above 0.9 and GRUB less than 1.99.x

I could be wrong, but I have read an awful lot of grub's mailing list and debian bug archives recently.

I'm going to remove my earlier post and put it in it's own thread as this could get confusing and I suspect my problem is different to the OP's.

---

### Post by ztrange on 2011-01-05
Ok, problem solved. What happened was that I was making the install with a USB pendrive and Ubuntu was detecting it as sda1... Don't know why but I just re-installed using a CDROM and everything is fine now.

It was a hardware RAID.

---

### Post by psusi on 2011-01-05
> **truant said:**
> From what I've read, not with RAID metadata levels above 0.9 and GRUB less than 1.99.x


That is correct.  Fortunately the default is 0.9.

---

