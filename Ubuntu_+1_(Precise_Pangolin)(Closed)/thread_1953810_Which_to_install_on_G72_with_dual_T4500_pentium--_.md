---
title: "Which to install on G72 with dual T4500 pentium-- i386 or AMD64"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Dngrsone on 2012-04-06
As noted in the subject line, I have an HP G72-259WM with dual Pentium T4500 and 8GB RAM.  I am currently running 10.04-desktop-AMD64.

So, do I run 12.04-desktop-AMD64 or would I be better served using 12.04-desktop-i386?

If the latter, then is there anything special I will have to do with my data when importing from the 10.04 64-bit desktop?

---

### Post by SemiExpert on 2012-04-06
> **Dngrsone said:**
> As noted in the subject line, I have an HP G72-259WM with dual Pentium T4500 and 8GB RAM.  I am currently running 10.04-desktop-AMD64.

So, do I run 12.04-desktop-AMD64 or would I be better served using 12.04-desktop-i386?

If the latter, then is there anything special I will have to do with my data when importing from the 10.04 64-bit desktop?

 Ubuntu is finally going to make 64-bit 12.04 the recommended version.  I'd advise running a Live Disc or trying 12.04 with Unetbootin.

---

### Post by mcellius on 2012-04-06
Several weeks ago Phoronix ran a comparison between 32-bit and 64-bit versions of Ubuntu, and found that the 64-bit performance was better.  Since your computer is capable of running the 64-bit, I suggest you do it.

When I first installed Ubuntu 11.04, I tried both and found that the 64-bit seemed slightly faster on my system, but I also found that I ran into no conflicts or problems at all.  These days, 64-bit is very stable, runs everything, and will make better use of your system's resources.  If you can run it, there is no reason not to do so.

---

### Post by Dngrsone on 2012-04-06
Thanks.

I was planning on running from the CD for a little while, at least, eventually installing to a new set of partitions (preserving my current 10.04 install).

---

### Post by mcellius on 2012-04-07
That sounds very reasonable.  In my case, I wanted to run 12.04 from a partition so I created one for it and installed it next to my 11.10 installation, and just dual-boot into whichever I want to run.  (These days it's almost always 12.04, as it's stable enough for me to do everything on it; your mileage may vary.)

I wanted to change icons, backgrounds, themes, etc., to test its response to customization, so I really needed a hard-drive installation.  I also wanted to be able to stay up-to-date with bug fixess and updates, for which a hard drive installation was also necessary.  Otherwise, there's no problem running it from a liveCD.

---

### Post by Dngrsone on 2012-04-07
Dang!  I managed to paint myself into a corner here-- I have the free space to install 12.04 in, but no free primary partitions...

Am I going to break 10.04 if I delete SDA3, make it an extended partition and then recreate swap?

I know I will have to unmount the swap file; then what, reidentify the new swap partition in fstab?

---

### Post by cariboo on 2012-04-07
You don't need to install Ubuntu on a primary partition, just use a logical partition. You also don't need to create a new swap partition, as Ubuntu is more than happy to share a swap partition with other installations. This is what my partitions look like on this system:

> sudo fdisk -l
[sudo] password for cariboo: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088c37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531775     9764864   83  Linux
/dev/sda2        19533822    23437311     1951745    5  Extended
/dev/sda3        23437312   117186559    46874624   83  Linux
/dev/sda4       117186560   312580095    97696768   83  Linux
/dev/sda5        19533824    23437311     1951744   82  Linux swap / Solaris

On this system, dev/sda1 is / /dev/sda3 is /home on my Ubuntu install, /dev/sda4 is an Xubuntu install, with dev/sda5 a shared swap partition for both installs. The partitioning scheme isn't what I'd do if I set the partitions up myself, but both installs where done for iso testing.

This is my netbook, which very rarely sees an installetion that lasts all the way through a development cycle.

---

### Post by Dngrsone on 2012-04-08
The problem is, I have to kill SDA3, which is the swap, absorb the unassigned space and turn SDA3 into an extended partition.

Then I can create the swap again, as say SDA9.

Meanwhile, I have to figure out what I have to do to keep my existing 10.04 installation from blowing up because the swap that used to be SDA3 is now SDA9.

---

### Post by xyzzyman on 2012-04-08
You'll just have to edit your fstab to point to sda9 for swap, and possibly run mkswap.

If you really did upgrade that unit to 8GB of RAM, you probably aren't ever going to touch swap anyways unless you use the hibernation feature. Being just a T4500 I can't see you doing anything super intensive that would also be RAM hungry.

---

### Post by Dngrsone on 2012-04-08
> **xyzzyman said:**
> You'll just have to edit your fstab to point to sda9 for swap, and possibly run mkswap.

If you really did upgrade that unit to 8GB of RAM, you probably aren't ever going to touch swap anyways unless you use the hibernation feature. Being just a T4500 I can't see you doing anything super intensive that would also be RAM hungry.

True, and the only reason I have 8GB of swap is because of the occasional hibernation, though Ubuntu doesn't handle that well, anyway.

You'd think I'd be able to do almost anything with this pig, but Minecraft lags heavy and for some reason OOo Base takes forever to load even a modest, 35 record database... 

So, anyway, I guess I will move my latest backup to the LAN drive and reallocate that partition later.

---

### Post by xyzzyman on 2012-04-08
> **Dngrsone said:**
> True, and the only reason I have 8GB of swap is because of the occasional hibernation, though Ubuntu doesn't handle that well, anyway.

You'd think I'd be able to do almost anything with this pig, but Minecraft lags heavy and for some reason OOo Base takes forever to load even a modest, 35 record database... 

So, anyway, I guess I will move my latest backup to the LAN drive and reallocate that partition later.

That's just a T4500 Pentium with integrated graphics, and probably the slowest hard drive that HP could throw in it so I'm not surprised. Usually the Walmart specific models are like that.

---

### Post by Dngrsone on 2012-04-08
Well, I managed to repartition the drive... I had to expand SDA4 to encompass the free space because gparted wouldn't let me make SDA3 an extended partition... and what's with the little 1MB blocks of unallocated space gparted drops?

... anyway, 12.04 is on, and now I get two separate grub boots, and I think Win 7 is broken...

Ah, the joy of installing new Operating systems...  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

---

