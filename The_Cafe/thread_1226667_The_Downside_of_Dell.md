---
title: "The Downside of Dell"
date: 2009-07-29
forum: The Cafe
---

### Post by nixscripter on 2009-07-29
This is just to vent a little. I believe it was on this very forum that Google showed me the solution, so thanks.

I bought a brand new Dell Inspiron 531s. Why? Because with an EPP discount from my employer, it was only $250. I knew it might be a little tricky to put Linux on it (it shipped with XP), but have fought with a lot of machines. Nothing I couldn't handle, right?

Well, this one takes the cake.

I juggled the partitions with Partition Magic, installed, and rebooted. It said:

```
Loading PBR for descriptor 2...
Bad PBR signature
```

Okay, I thought, so grub didn't go in right. Reboot from CD, manually install grub in the right place. The result:

```
Loading PBR for descriptor 2...
Bad PBR signature
```

I look at the partition table to discover partition magic scrambled it pretty well. I unscramble it by hand with **gparted**, wipe everything, reinstall all over again, taking about 2 hours. Guess what happened:

```
Loading PBR for descriptor 2...
Bad PBR signature
```

Something else was going on. After another hour of searching the internet, I made quite an interesting discovery:

> 
There was nothing wrong with my partitions at all. Dell just gripes because it wants to see a FAT16 or FAT32 or NTFS partition somewhere. If it doesn't see one of these on the "boot" disk, the BIOS simply crashes out.

Again, there was nothing wrong with Windows or Ubuntu at all, just Dell's BIOS refusing to cooperate.

"Loading PBR for descriptor 1...
Bad PBR signature"

on a Dell after a Ubuntu install should be translated

"Dell doesn't support non-Windows operating systems...
and we enforce that in our BIOS" 


So, after a little bit of swearing at it, I changed the boot partition to FAT32. Sure enough, everything worked.

I have never seen anything like it. I suppose I could see why they did it -- if things are corrupted the BIOS could detect that -- but it violates the PC architecture and is incredibly stupid. Besides, I thought Dell was one of the good guys -- guys who will ship Linux on some things. I have a Dell laptop I bought 3 years ago, Ubuntu pre-installed, which works well (except for a few 3-D graphics issues). But then, they go pull a stunt like this.

Anyway, I'm not buying any more Dells. I guess my sig line says it all.

---

### Post by dragos240 on 2009-07-29
Try an open source bios. Yes there are a few.
Like coreboot or openbios.

---

### Post by DeadSuperHero on 2009-07-29
Wow, I didn't realise Coreboot could run on Dell products.

I'd hope to one day see Coreboot on some of their laptops, though!

---

### Post by utnubuuser on 2009-07-29
This guy could use some help with the whole DELL thing.
> [http://dellhellrevisited.blogspot.com/]("http://dellhellrevisited.blogspot.com/")

---

### Post by MikeTheC on 2009-07-29
Wow. I would probably use the recovery disc to set the system back up to factory defaults and then just return it and buy something else. Perhaps I'd also include a letter with the machine telling them why I was returning it, and that I didn't appreciate them doing that with their BIOS.

But then again, that's just *me*. YMMV.

---

### Post by BillHudson on 2009-07-29
"Wont work unless FAT16 or FAT32 or NTFS partition"

I am new to Ubuntu and am wondering what kind of partition was you trying to use that was a problem? I thought I saw somewhere about another FS that it used but I just put it on my Dell with NTFS thinking it might not work with it, of course it did so I just went with it.

I'd like to read up on that file system though.

---

### Post by PhoHammer on 2009-07-29
> **MikeTheC said:**
> Wow. I would probably use the recovery disc to set the system back up to factory defaults and then just return it and buy something else. Perhaps I'd also include a letter with the machine telling them why I was returning it, and that I didn't appreciate them doing that with their BIOS.

But then again, that's just *me*. YMMV.

I'll probably never buy a Dell due to this and other reasons, so it'll end up hurting their business in the long run (or short run, as I am in the market for a new laptop right
now...)

---

### Post by MasterNetra on 2009-07-29
Then don't buy dell. Go to system76.com it may not look like it on the surface but after comparing with dell, you can for sure get more for less there. I should of tried seeing If i could get a student loan to use at system76 rather then this crappy school set labtop, which adds $1500 to my tuition. (750, just what is called the "Idiot Warranty" a 3 year warranty where should something go wrong you can get it fixed/replaced free)...Though frankly I could find a better laptop (with a DVD-RW drive added) at system76 for $444...learned my lesson..

---

### Post by Yes on 2009-07-29
> **BillHudson said:**
> "Wont work unless FAT16 or FAT32 or NTFS partition"

I am new to Ubuntu and am wondering what kind of partition was you trying to use that was a problem? I thought I saw somewhere about another FS that it used but I just put it on my Dell with NTFS thinking it might not work with it, of course it did so I just went with it.

I'd like to read up on that file system though.

Linux (and I'm assuming Ubuntu) can run on a variety of different file systems.  The most common is ext3, but there's also ext4, reiserFS, XFS, JFS and I think there's a few other more obscure ones out there.  And then you could also use the Windows file systems, fat32 and NTFS.

---

### Post by sdlynx on 2009-07-29
thats ridiculous!!! wow DELL way to go.

---

### Post by dragos240 on 2009-07-29
Good thing I didn't convert my moms comp.

---

### Post by nixscripter on 2009-07-30
Thanks for the sympathetic disgust.

1. I am going to re-sell it second hand. It was designed to be a cheap computer, but a cheaper one which does what I want has walked into my life. And it has a nice, **dumb** BIOS.

2. I didn't think coreboot worked on Dells either. Based on the internal diagnostics you can run at the end of the setup screen, and the complexity of low-level junk they use (including the Tech Support serial number!) I'm not going to risk this one.

3. The reason I wanted to use EXT for everything was because FAT requires extra code pages (character sets built into the kernel), and doesn't allow symbolic links, which really sucks. The first thing GRUB normally wants to do is two symlinks, so I had to work around that too.

4. It's sort of a shame, beacuse it also took me a while to get the nVidia PCM61 chip working with graphics (including 3-D), and sound (apparently, there's a Realtek chip in there!?), and ethernet (the driver was knocked out of version 2.6.29 due to hibernation issues irrelevant to me). I consider that a reasonable achievement.

My general rule for desktops is to build it myself. I'll stick to that in the future.

---

