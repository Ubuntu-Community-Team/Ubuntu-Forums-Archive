---
title: "Live CDs have NO effect right?"
date: 2008-10-26
forum: The Cafe
---

### Post by NintendoTogepi on 2008-10-26
I'm gonna try Puppy on my good computer.

As soon as I turn off the computer and take out the CD its like it never happened, right?

I might try the Ubuntu Live CD too...

---

### Post by Corfy on 2008-10-26
LiveCDs have no effect... unless you tell it to.

For example, the Ubuntu LiveCD has an "Install" icon on the desktop. Clicking on that and following through the prompts will effect your harddrive.

Also, you can connect to your harddrive and add, delete, or edit files. I use this feature with LiveCDs a lot when working on fixing broken Windows systems. But it is pretty obvious that you are connecting to your harddrive.

---

### Post by chris4585 on 2008-10-26
deleted - thought he was talking about compiz ](*,)

---

### Post by MaxIBoy on 2008-10-26
It depends on which liveCD you choose-- I know of at least one liveCD (SuSE) that mounts existing filesystems and creates pagefiles in them. But that's understandable, because SuSE is incredibly bloated.

---

### Post by ukera on 2008-10-26
LiveCD's don't have an effect, that's why their called "LiveCD's".. :P
When you boot up ubuntu you have a few options, one is install ubuntu, another one is boot up ubuntu with no changes done to your computer..  check it out.

-ukera

---

### Post by lukjad on 2008-10-26
LiveCDs are like operating systems installed in RAM. They can have a BIG effect if you tell them to. Just like you can dual-boot Linux and XP, you can, from your Linux side, start deleting and renaming files on the XP partition. If you do that, then you can cause damage. If decide to install this LiveCD, you can damage your system simply by erasing it. 


Simply put: Don't do anything, like deleting a file, you wouldn't do elsewhere. Then all should be fine. 

Also, Puppy Linux has an option to save the session. DON'T DO THIS on a bootable Linux partition! It can and WILL give you headaches. I did this once. ONLY save it on a Windows/FAT/FAT32 Partition.

---

### Post by forrestcupp on 2008-10-26
But like MaxIBoy said, some of them put page files or config files on your hard drive, which means that in those cases it's possible to tell that someone ran a livecd.  But no, it won't alter your installed OS.

---

### Post by MaxIBoy on 2008-10-26
On the other hand, if your liveCD creates a pagefile, you had better make *absolutely* sure you shut it down properly. I'm not sure what fsck or chdsk will do in reaction to corrupted files that were created by a different OS (especially pagefiles!)

---

### Post by zekopeko on 2008-10-26
i don't think ubuntu or opensuse do "pagefiles" to the drives. but i know that the liveCD will mount an existing swap partition.

---

### Post by chucky chuckaluck on 2008-10-26
haha! this is *exactly* the type of thing i used to, and still worry about. save your file cards, my friend. our time's a-comin'!

---

### Post by FuturePilot on 2008-10-26
> **MaxIBoy said:**
> On the other hand, if your liveCD creates a pagefile, you had better make *absolutely* sure you shut it down properly. I'm not sure what fsck or chdsk will do in reaction to corrupted files that were created by a different OS (especially pagefiles!)

What? Pagefiles? Live CDs don't touch the hard drive unless you tell them to. Also Linux does not use pagefiles. It uses a swap partition instead, so a Live CD is not going to mount your partitions and write random stuff to them. The only thing it *might* do, and this completely depends on you already having a Linux install on your hard drive, is mount the swap partition. If a Live CD is mounting your partitions and writing random garbage to them I would consider that a bug.

> **forrestcupp said:**
> But like MaxIBoy said, some of them put page files or config files on your hard drive, which means that in those cases it's possible to tell that someone ran a livecd.  But no, it won't alter your installed OS.
I have yet to come across a live CD that has written something to the hard drive without me telling it to.

---

### Post by MaxIBoy on 2008-10-26
> **zekopeko said:**
> i don't think ubuntu or opensuse do "pagefiles" to the drives. but i know that the liveCD will mount an existing swap partition.

Yes, it will, but that's harmless. (But what if something else has hibernated?)

---

### Post by init1 on 2008-10-26
In theory, a Live CD could alter your hard drive with you telling it to. But in reality, most if not all Linux Live CDs will leave your hard drive alone, save for any swap partitions your have.

---

### Post by DougieFresh4U on 2008-10-26
I had tried 'Puppy' about a year ago, and I thought that it did leave the settings on your hard drive in a file some where. but I could never find the file :confused:

---

### Post by cardinals_fan on 2008-10-26
> **DougieFresh4U said:**
> I had tried 'Puppy' about a year ago, and I thought that it did leave the settings on your hard drive in a file some where. but I could never find the file :confused:
Only if you tell it to.

The only ways a live CD can cause lasting harm are:

a) If you tell it to ;)

b) In a few rare cases, hardware can be bricked by certain kernel versions.  An openSUSE alpha a few weeks ago included a very new kernel version that bricked a model of wireless adapter.

---

### Post by TBOL3 on 2008-10-26
By definition, a liveCD shouldn't leave MUCH of a lasting effect.

However, any cd that you enter, can do almost anything (within the limits of reality) to your computer.  The real question is, is the cd your putting in a live cd?

---

