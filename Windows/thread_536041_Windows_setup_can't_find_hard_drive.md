---
title: "Windows setup can't find hard drive"
date: 2007-08-27
forum: Windows
---

### Post by jaymz on 2007-08-27
I have Ubuntu Feisty installed, I'm really happy with it, I just need a tiny little instalation of Windows so I can game a little...

The problem is since I installed Feisty I can't reinstall Windows! When I insert the Live CD for XP or Vista (I don't really care which one I have, I just want it so I can play PES 6) the Windows setup tells me I have no hard drive connected.

Which is ludicrous, I do, I'm on a laptop! I have Ubuntu installed and it's working fine.

Any idea? This is just weird, never happened to me before...

---

### Post by jnorthr on 2007-08-27
Just a guess here, but you may have installed ubuntu with all your partitions as ext3 and there are no FAT32 type partitions for the windows install disk to 'see'. Can you create a FAT32 partition with a few gigs just to see if the install will notice it ? Note that if that works and you install xp/vista it may wipe the grub loader out of the master boot record, then you will only 'see' windows and it will look like ubuntu has dis-appeared - unlikely. You may need to reinstall supergrub then to be able to see both o/s. This is known as 'dual-boot'.

---

### Post by jaymz on 2007-08-29
Aaaah! I totally forgot that windows doesn't like ext3... Why don't I remember that windows doesn't like anything that it doesn't make itself?

Ah well, thank you very much, that has to be it. I'll get back to you once I've got it going.

And I know that Windows removes grub and what dual boot is :P

I'm not that much of a n00b

oh and btw, which program do you recomend to part my disk? Gparted?

---

### Post by phenest on 2007-08-29
I also have/had this problem. I can install Ubuntu, Windows 98SE & Vista, but XP says it cannot find the hard drive. This is a Philips freevents X56 if anyone can help. I want to re-install the original XP so I can sell it, because I don't like it. Very Linux unfriendly. But I don't have the proper install CD's. I'm trying a friends XP which won't install. And I only have the 30-day trial of Vista.

---

### Post by phenest on 2007-08-29
I just had a thought: this laptop has a SATA hard drive. I need the drivers prior to installation. Don't know where to get them, or why 98SE was ok. And I don't have a floppy drive.

---

### Post by rickyjones on 2007-08-29
> **phenest said:**
> I just had a thought: this laptop has a SATA hard drive. I need the drivers prior to installation. Don't know where to get them, or why 98SE was ok. And I don't have a floppy drive.

You'll need to download the drivers from the manufacturers website. If you don't have a floppy drive then you'll need a USB floppy drive most likely.

-Richard

---

### Post by jaymz on 2007-08-31
OK, so I tried jnorthr's solution to no success...

I now have a 10 gig FAT32 partition on my hard drive and still windows can't "see" it.

It just annoys me not to be able to game a little when taking a break from work, I don't really need Windows.

(also I hate this kind of situations when I can't understand what I'm doing wrong)

Any help would be very apreciated :)

---

### Post by phenest on 2007-09-01
Do you have a SATA hard drive? If so, see my post above.

---

### Post by jaymz on 2007-09-01
Yep, it's a SATA...

So what am I supposed to do now? I have to get a USB floppy drive? (no, my computer doesn't have one...)

---

### Post by rickyjones on 2007-09-02
> **jaymz said:**
> Yep, it's a SATA...

So what am I supposed to do now? I have to get a USB floppy drive? (no, my computer doesn't have one...)

Yup - unfortunately Windows XP doesn't have drivers for a lot of SATA devices out there. The only way to load them is via a floppy drive during installation or you can slipstream the drivers into your install CD. I would think borrowing a floppy drive would be easier.

-Richard

---

### Post by phenest on 2007-09-02
Not that I've tested this, but I have heard that only internal floppy drives are recognised by the XP installer and not USB ones. I have a USB floppy drive that I'll test when I have time. Can anyone confirm this is the case?

---

### Post by morno on 2009-01-14
im having the same problem. i will post here again if i find a selution.

---

### Post by rickyjones on 2009-01-15
> **phenest said:**
> Not that I've tested this, but I have heard that only internal floppy drives are recognised by the XP installer and not USB ones. I have a USB floppy drive that I'll test when I have time. Can anyone confirm this is the case?

I've used USB Floppy Drives to boot Windows. It does indeed recognize it as long as the BIOS passes it off as a floppy disk drive.

Thanks,
Richard

---

### Post by phoenixphyre on 2009-01-15
> **jaymz said:**
> Yep, it's a SATA...

So what am I supposed to do now? I have to get a USB floppy drive? (no, my computer doesn't have one...)

I talked with a local computer store in my community, and one of the techs said that it doesnt matter what you do, windows doesn't like Macintosh or Linux. you can mesh Mac and Linux but not with windows. as a matter of fact, he said that if you have linux installed on your machine as a primary DO NOT LOAD WINDOWS. I tried it out a couple of weeks ago and windows erased all of my information, partitions, and everything and i had to start Ubuntu all over again. FORGET WINDOWS. try to find emulators for linux for gaming, they do exist.

---

### Post by rickyjones on 2009-01-15
> **phoenixphyre said:**
> I talked with a local computer store in my community, and one of the techs said that it doesnt matter what you do, windows doesn't like Macintosh or Linux. you can mesh Mac and Linux but not with windows. as a matter of fact, he said that if you have linux installed on your machine as a primary DO NOT LOAD WINDOWS. I tried it out a couple of weeks ago and windows erased all of my information, partitions, and everything and i had to start Ubuntu all over again. FORGET WINDOWS. try to find emulators for linux for gaming, they do exist.

Kind sir, I believe that you are only about half right with this information.

You are correct that the Windows installation routine does not play nice with other operating systems other than earlier version of Windows. The installation of Windows in an existing environment will install a new bootloader which will make it difficult to get back into your previous operating system.

When you install Windows you select which partition you will install it on. Unfortunately this partition manager is not as advanced as GParted but it works great if you have an unpartitioned area of your disk. The installation will not just install on any partition it sees - the user chooses where it installs - unless your media has an auto-installation script which may modify these parameters.

Linux and Windows can easily coexist, even if you install Windows last.

If you are going to do a dual boot then I highly recommend planning it out before hand and setting up all necessary partitions before loading either operating systems. For example, this is how my hard disk was configured for my last dual boot experience.

Total size: 120GB
Partition 1: 40GB, Windows C:\, Primary Partition
Partition 2: 40GB, Linux root, Logical partition
Partition 3: 2GB, Linux swap, Logical partition
Partition 4: The Rest, Windows H:\ for My Documents, Logical Partition

I installed Windows first and then Ubuntu. This worked quite well for my needs.

Thanks,
Richard

---

