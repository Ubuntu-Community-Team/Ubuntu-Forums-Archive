---
title: "Brand New, easy to install, what a snap."
date: 2007-01-26
forum: Testimonials &amp; Experiences
---

### Post by snakepimp on 2007-01-26
Hello, I have never used Linux before, but I just installed a dual boot with WindowsXP successfully in the same amount of time (not including Download time and burning image to disc.) it took my girlfriend to get ready to leave the house, don't be scared. 
I do have some technical knowledge, but, umm, you wouldn't need it.
I left about 30GB unallocated on my C: drive when I installed Windows. I made a 30GB Fat32 partition on another physical disk, I let cavalierly let Ubuntu detect defaults for disc partitioning, and it installed exactly the way I wanted it, too, lookee there, works great. I can't say it would work for you, but if you know Windows disc management utiity at all, you should be able to figure out the partitioning for this install.

I installed 6.10 Edgy Desktop standard Build.
I am running AMD Barton Core 2500+
Biostar M7NCD Nforce2 Mobo
ATI All-in-Wonder 9600 Pro (haven't tested 3D yet...)
I am making this post from Ubuntu, the networking was a snap.
Windows still boots and runs, and I'm happier than a porcine in excrement.
Don't be scared, fellow n00blet, just lurk on these forums for a couple of days, like I did, learn the basics, and let 'er rip!

---

### Post by taurus on 2007-01-26
Congrats and welcome.  Will move this one over to Testimonials.  ;)

---

### Post by Pobega on 2007-01-26
I think this belongs in Ubuntu testimonials, but congrats on getting it to work :)

I had ease my first time too, it just works for some people I guess.

---

### Post by snakepimp on 2007-01-28
Proof that I'm a newb, posted in the wrong forum.

I actually have installed Ubuntu 3 times now. I installed Edgy Desktop, Edgy Server (ran from CLI for a while, it was a new game...) and Dapper Desktop, all dual booted with WindowsXP, I just deleted the Linux partitions, ran fixmbr (to remove GRUB and restore Windows' boot.ini loader...) from Windows CD, then reinstalled each time, I haven't had a lick of problems.
I don't know if this is right or advanatageous, or what not, but I have 3 hard disks, partitioned like this:

Partition info: 

ATA100, IDE controllers=2 

    * Hard Disk 1, Master IDE0 (hda)
    *     Partition1 NTFS 80GB
    *     Partition2 ext3 24GB
    * Hard Disk 2, Slave IDE0 (hdb)
    *     Partition1 NTFS 233GB (WinData)
    * Hard Disk 3, Master IDE1 (hdc)
    *     Partition1 NTFS 84GB ProTools Audio 
    *     Partition2 FAT 24GB For Win32/Linux Sharing.
    *     Partition3 linux-swap 4GB
    * CDRom, Slave IDE1

---

