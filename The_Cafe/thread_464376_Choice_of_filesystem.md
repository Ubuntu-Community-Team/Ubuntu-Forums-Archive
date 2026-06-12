---
title: "Choice of filesystem?"
date: 2007-06-04
forum: The Cafe
---

### Post by juxtaposed on 2007-06-04
This is another generic "I like this, what do you like?" thread.

Wondering what others choice of filesystem is like, and why; I'm thinking of switching my FAT32 500GB external hard drive to a better filesystem, and i'd like to do it before I get any more stuff on it that would make it harder to use. I'm thinking ext3, but i've heard about others that might be better (like reiserfs or something). Of course, it needs to be windows compatable - there is a program that lets you see/change/write to files on an ext3 file system in linux, though i've heard it can corrupt easily.

So, reading others answers on this semi-poll will help me decide.

Currently I use ext3 on linux, and NTFS on windows.

---

### Post by visionaire on 2007-06-04
i have used reiserfs and is damn fast!

---

### Post by Mazza558 on 2007-06-04
I use Ext3 on linux, Ext3 as a shared partition between XP and Linux (with all windows games/apps installed here), and a 10 GB partition for Windows (NFTS)

---

### Post by juxtaposed on 2007-06-04
[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

This looks interesting, as it is said to have good performance.

I'm also thinking of encrpyting my filesystem; unless it leads to big problems (like speed or compatability).

---

### Post by jclmusic on 2007-06-04
i use ext3, and fat32 on my second hard drive because it needs to windows readable - i swap it around a lot.

---

### Post by a12ctic on 2007-06-04
I use XFS most of the time, its a lot faster than ext3.

---

### Post by speedygeo on 2007-06-04
I use FAT 32 on winxp partition, but I primarily use Kubuntu on a reiserfs. The /home partition is on a reiserfs too. I had problem with ext3 when I access it from win, so I don't access anymore. I access the FAT32 easily from linux.

---

### Post by mips on 2007-06-04
Mostly XFS but would love to give ZFS a spin.

---

### Post by juxtaposed on 2007-06-04
> I use XFS most of the time, its a lot faster than ext3.

> Mostly XFS but would love to give ZFS a spin.

XFS sounds good, I should consider trying it.

How easy is it to access it from windows? Is it possible to encrypt it without a total loss of performance?

---

### Post by ynnhoj on 2007-06-04
i stuck with ext3 for quite a while, but made the switch to reiser the last time i re-installed (~3 months ago).  i didn't think xfs would be mentioned so many times -- i guess i'll read up on it to figure out why :)

---

### Post by yatt on 2007-06-04
> **juxtaposed said:**
> XFS sounds good, I should consider trying it.

How easy is it to access it from windows? Is it possible to encrypt it without a total loss of performance?

I use it too, and as far as I know, there isn't a Windows driver for it.

---

### Post by a12ctic on 2007-06-05
> **juxtaposed said:**
> XFS sounds good, I should consider trying it.

How easy is it to access it from windows? Is it possible to encrypt it without a total loss of performance?

duno havnt used windows sense 2001 on my desktop.

---

### Post by LightB on 2007-06-05
I use JFS. It's supposed to use less resources when writing large files.

---

### Post by the_darkside_986 on 2007-06-05
I use ext3 since I'm not sure what else I should use on Ubuntu. In openSUSE, it installed reiserfs by default but I can't tell the difference in speed on my system. I also use UFS on my FreeBSD partition because it is the default choice when installing. I have no Windows compatible file systems except a Fat32 on a portable usb drive and psp memory card.

---

### Post by runningwithscissors on 2007-06-05
I use JFS for my home partition and ext3 for everything else (boot/root/usr/var/portage tree).

Never had any problems with any of them.

I had used ReiserFS (back when it was still maintained) on a few image files. And some of my files in it were corrupted due to sudden power loss while the image was mounted.

---

### Post by frodon on 2007-06-05
ext3 by default (80% of my total disk space), fat32 for my game partition and my external usb disk

---

### Post by steeleyuk on 2007-06-05
EXT3 on both hard drives. Never causes any problems for me...

---

### Post by mips on 2007-06-05
> **juxtaposed said:**
> 
How easy is it to access it from windows? Is it possible to encrypt it without a total loss of performance?

I'm not aware of windows being able to access XFS partitions at all but maybe have a look at this:
[http://www.crossmeta.com/crossmeta.html](http://www.crossmeta.com/crossmeta.html)
[http://www.soft32.com/download_190903.html](http://www.soft32.com/download_190903.html)


Never tried encrypting a XFS partition so I honestly cannot say.

---

### Post by speedygeo on 2007-06-09
ZFS is presented like the best fs. Exist a way to use it in Kubuntu/Ubuntu?

---

### Post by angryhomer17 on 2007-06-09
ext3. Used that ever since I switched to linux. No probs with it. Stable. I see xfs being mentioned a lot. How's that work out? I have an 300 gig external hdd with a lot of flac files (some mp3 :( ) When I build my new system I think I'm going to transfer all my music to a 500 gigs sata drive. Perhaps xfs is a better choice the ext3 for flac files?

---

### Post by zenwhen on 2007-06-09
EXT3 for my /home partition where my important files go, and Reiser 3 for my root partition, since my actual install can be easily replaced, and Reiser is faster.

---

### Post by NeoLithium on 2007-06-09
> **juxtaposed said:**
> [http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

This looks interesting, as it is said to have good performance.

I'm also thinking of encrpyting my filesystem; unless it leads to big problems (like speed or compatability).

It does give good performance, I have my /home and my /data partitions as XFS. :) No complaints in the least :)  The root filesystem is still ext3 though

---

### Post by insane_alien on 2007-06-11
yeah but with XFS if it borks it borks all the way. you don't get your data back.

---

### Post by thisllub on 2007-06-11
I have a Reiser home partition that has made it through over 2 years and more than a dozen distros but the future looks bleak for Reiser as Hans Reiser has been charged with his wife's murder.
[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

---

### Post by juxtaposed on 2007-06-11
I just installed ubuntu (had debian before, wanted to go back to ubuntu) and I used XFS (with a 512MB /boot as ext3) and it seems to run great.

---

### Post by SunnyRabbiera on 2007-06-11
ext3 as its the usual default for linux, if others are available I dont bother with them

---

### Post by Adamant1988 on 2007-06-11
I use XFS on my desktop because I run virtual machines.  XFS can read and move HUGE files VERY quickly, giving me added performance when reading from a VMware file, etc.  Which is just plain important to me. 

I would really like to see what ZFS can do for me, but I don't suspect I'll see that until I get my macbook or macbook pro next year once I get stationed.

---

### Post by Al Fairclough on 2007-06-11
> **thisllub said:**
> I have a Reiser home partition that has made it through over 2 years and more than a dozen distros but the future looks bleak for Reiser as Hans Reiser has been charged with his wife's murder.
[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

Yup, that Reiser will kill ya.  ;)

---

### Post by thechris on 2007-06-11
I normally use XFS, but for ubuntu i get blocked by the installer.  It always tells me that I MUST put / /usr /boot on ext2/3.  This makes no sense as XFS works on all of these.  In anycase, maybe its an issue with the installer for AMD64.  I've had this issue back with ubuntu6 as well and solved it by simply moving the install to a different partition that had the correct FS on it.

---

### Post by roachk71 on 2007-06-11
XFS all the way:

On this computer, I have a 50 GB NTFS partition for XP (need that for my emulators) and the rest as XFS for my Ubuntu partition (save the 1.5 GB or so for the swap.)

XFS is fast & efficient and, if you're careful enough, it shouldn't crash terribly.

Oh, and I know hot to do this, but I wonder whether or not anybody has written a howto for reprofiling the system boot using LILO yet, since I'd like to share this... :KS

---

