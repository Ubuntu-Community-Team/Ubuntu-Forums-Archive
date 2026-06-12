---
title: "Want exFAT support by default in Ubuntu?  Then see this bug and add your support."
date: 2015-12-28
forum: The Cafe
---

### Post by MechaMechanism on 2015-12-28
If this bug effects you then click on "Does this bug affect you?"

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1434603](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1434603)

---

### Post by kurt18947 on 2015-12-28
As I understand it, Microsoft was pretty liberal with permitting others to implement FAT & FAT32. As a result they became defacto standards with little revenue to Microsoft. MS has a bunch of patents around ExFAT and intends to keep closer tabs on users of ExFAT to make sure they get paid every dime they're due. I don't know the legality of those packages in the U.S. or elsewhere.  If Canonical or Red Hat began including them in their distros by default I wonder if Microsoft might claim a patent violation and either demand licensing $ or removal of those packages from the distro **and** the repository.  If there's any uncertainty about the legal status of ExFAT support I'd rather go through an extra step to enable support rather than not have it easily available at all. 

I read once (don't remember where) that device manufacturers pay Microsoft $300,000 per model for the right for their device to read and write EXFat files. This was part of a discussion about why not use an free file format such as ext2 for large capacity flash devices rather than a patent encumbered standard like ExFAT. The reason given is that ext2 is not natively supported by Windows, EXFAT is. There are drivers for Windows that will enable Windows to read and write ext files.  If such software were made available by hardware manufacturer XYZ against Microsoft's wishes, how long would it take for a Windows 'security update' to break those drivers so customers couldn't easily use XYZ'S hardware writing ext2 files? Of course customers having trouble moving digital content from brand XYZ hardware to their Windows PC are going to blame XYZ, not Microsoft.

---

### Post by yoshii on 2015-12-28
Why not format those portable drives as NTFS if you really need the cross-compatibility?  Most Windows users don't even use ExFAT.  I played around with it back in my Windows days, but most of my Windows maintennance programs didn't support it.  FAT32 is just easier since it's so old and well understood (including for it's limitations).  I know ExFAT might have some minor advantages for flash media, but if it was really all that great, I think the flash media companies would put pressure on the rest of the industry to change to it and they'd provide flash media preformatted with it.  

Even if you're using a Mac, FAT32 works out OK, while NTFS is still a hurdle without some special changes.  So I know NTFS isn't perfect.  

I do acknowledge though, that for NAND technology, some of the newer filesystems do "garbage collection" better and stuff like that.  I think even ext4 has some improved provisions for that, but of course then you have the same issue of cross-compatibility as soon as you stick that flash drive into the average Windows computer.

---

### Post by kurt18947 on 2015-12-29
```
Most Windows users don't even use ExFAT.
```

If Windows users have flash devices of 64 GB. or larger, I'll bet they do. They just don't know it. And that's an advantage, it's transparent.

---

### Post by Bucky Ball on 2015-12-29
Believe it or don't, many audio/video devices only use FAT32 formatted SD cards. Same with the Raspberry Pi OS card. Pretty sure Boot Repair and others need a FAT32 formatted SD. I use UNetbootin to create USBs of all sorts and they all need to be in FAT32. 

So, FAT32 is still used. Just not for SSDs and HDDs, internal or external, unless it is for a specific purpose (although I can't think of one).

@MechaMechanism: Have you opened a thread on this here? Might be a good idea and get you some help rather than asking people to report a bug it seems only you and two other people have reported since March.

---

### Post by 1clue on 2015-12-29
At one point this exfat support thing really bothered me.  Then I worked a few things out:

[LIST=1]
[*]Almost all of my commercial OS access is owned by some other party, meaning I don't have/own the box.
[*]I don't know of a single Linux distro which does not allow easy installation of exfat support.
[*]I use a lot of distros.
[*]The first thing I do with most non-source distros is uninstall a bunch of stuff I don't want.
[*]The second thing I do with most non-source distros is install the few things I do want.
[*]I'd rather add packages than remove them, it's much cleaner that way.
[/LIST]

Given that I have to tailor my Linux distro to what I want anyway, I'm extremely OK with having to install exfat support.

---

### Post by DuckHook on 2015-12-29
> **1clue said:**
> Given that I have to tailor my Linux distro to what I want anyway, I'm extremely OK with having to install exfat support.I'm with you on the general idea of adding rather than subtracting, but the problem is that it's another obscure hurdle for new users. The first time I bought a 64GB SD card, it was exFat which obligated me to learn about the exFat driver, FUSE and all the exFAT rigamorole in general. Since I love that sort of digging, it wasn't a chore for me, but I can easily see how it would not only be a chore, but an intimidating frustration for someone with little interest in the techie down-and-dirty.

I solved the problem permanently by reformatting the card to ext2 (thus avoiding bloat, yet another driver, and the security exposure of FUSE), but how many typical users want to go to such trouble? They just want plug and play.

---

### Post by 1clue on 2015-12-29
I've been using Linux since 1996. Compared to what a mainstream distro was like then, there are very few modern distros which are not incredibly easier.

That said, I've often needed to just get the job done, and wished for an automatic driver detector/locator feature.  For example, plug in the sdxc card, and the operating system detects that it contains an exfat partition and that no suitable driver is installed.  Pop up a dialog asking if the user wants to look for a driver, if they click yes then they get another dialog with suitable software.

Frankly that's what Windows does, so on a beginner distro like Ubuntu I see no harm in that sort of thing.

---

### Post by DuckHook on 2015-12-29
> **1clue said:**
> ...Pop up a dialog asking if the user wants to look for a driver, if they click yes then they get another dialog with suitable software...Good idea. Maybe Canonical is looking into something like that already. Love your signature BTW.:D

---

