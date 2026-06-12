---
title: "Corrupted Ext3 fs, New server, Many questions"
date: 2008-02-04
forum: Server Platforms
---

### Post by Gruelius on 2008-02-04
Hi all,
I have allways noticed small glitches in files and shrugged it off, thinking that they were there when i got them in the first place.
I recently got a big error when ifscked the volume, and i noticed big glitches before that.

Anyway i need to find out what caused it, so in my new system it wont happen.
Server:
AMD X2 3800+
6x200GB seagate IDE disks.
2x Silicon 680 PCI raid cards (passthrough mode i think)
Asus M2N.
Ubuntu 7.10

Mdadm says its array is fine, so it leads me to believe its software related.

Anyway i have no f**king clue where to start. Im not pissed off at anyone at ubuntu or linux in general, im just pissed off :(

For my new server i was thinking
Raid1 320gb sata disks for the os + Misc data array
Raid5 3x750gb sata disks for the data array.

My problem is that i need to find a sata controller from [www.scorptec.com.au](www.scorptec.com.au) for less than $200 with 4 sata 2 ports if possible. Whenever i search the ones with silicon image controllers up i just find tales of woe. So could someone suggest me one that wont give me issues?

My current IDE controllers give me the shits, smartd and smartctl dont work for some reason.

Thanks

---

### Post by cdenley on 2008-02-05
Have you checked your memory using the memory tester from the grub menu? Have you checked your hard drives for bad sectors? Is it one volume you consistently have problems with, or both?

---

