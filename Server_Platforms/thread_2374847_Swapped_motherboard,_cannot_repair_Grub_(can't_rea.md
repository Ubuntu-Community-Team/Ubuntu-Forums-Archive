---
title: "Swapped motherboard, cannot repair Grub (can't read superblock)"
date: 2017-10-19
forum: Server Platforms
---

### Post by dulcow on 2017-10-19
Hi there,

I have sent my ASRock C2750D4i for RMA last month and I have just received the new one a few days ago. After reassembling everything, it seems that I cannot boot up my machine any more :-( I have not changed anything else, the hard drives are plugged into the same SATA ports, BIOS configurations should be more or less the same. I have tried several things and I will summarize where I am now.

**What's cooking when booting?**
To keep it short, this: [http://dedef.info/files/IMG_0605.JPG](http://dedef.info/files/IMG_0605.JPG)

**Manual Grub repair**
Booting from a Live CD, I have tried to repair manually Grub. First step is to mount the /dev/sda1 (first partition of my Crucial 256GB SSD) which contains the OS. I can see the partition with "fdisk -l" but I cannot mount it, I'm ending up with the following error:

mount: /dev/sda1: can't read superblock

I have also tried to repair the filesystem. First the main node, then I tried with the backup ones: [LEFT][COLOR=#333333][FONT=&amp]fsck -b 32768 /dev/sda1[/FONT][/COLOR][/LEFT]

Same results...

**Boot-Repair - [http://paste.ubuntu.com/25774723/](http://paste.ubuntu.com/25774723/)**
From a Ubuntu Desktop Live CD (Ubuntu 16.04.3 LTS), I installed Boot-Repair and tried to run it. From the BIS report, it seems that I'm running into the exact same problem as above.

As funny as it might seem, I cannot find any of my backups... Meaning that I'm likely to have to reinstall the entire system very soon, something that I'm not particularly looking forward to be fully honest...

I suspect the GRUB v2 is messed up somewhere but I have no clue how to repair it. The worrying part is that I cannot mount any of my hard drives when booting via a Live CD.

Anyone would have a genius idea?

Cheers,

Dulcow

---

### Post by darkod on 2017-10-20
Reinstalling grub (even if you have to do it from scratch), is the easiest thing to do... But your problem seems to be worse. Not being able to mount partitions in live mode is definitely not a good sign.

What exactly happened to the old MB? Could it have damaged the ssd when failing?

Have you tried connecting the ssd to another machine and read it, just to confirm it opens correctly?

---

### Post by dulcow on 2017-10-20
Hey Darkod,

Good catch, I have continued tonight and I'm both happy/sad at the same time:

- Data from SnapRaid is intact on all the data drivers. I managed to mount those drives and browse through the files with SystemRescueCD.
- The bad news is that the SSD has fried. I changed the port and SATA cable, same. I tried it on my Windows machine, I cannot even format it.

The mobo stopped working one month ago, from one day to another. It's a known hardware issue from the Intel C2750. ASRock has replaced for free the motherboard. I will replace the SSD tomorrow but I need to chose again a distro and I'm tempted by FreeNAS to finally stop playing in command line...

Thanks again for the steer,

Cheers,

G.

---

### Post by darkod on 2017-10-20
No problem. If you consider this solved please mark it as solved in Thread Tools above the first post. Cheers...

---

