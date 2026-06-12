---
title: "Noticed a commonality between Ubuntu &amp; Windows XP"
date: 2007-11-30
forum: The Cafe
---

### Post by Scruffynerf on 2007-11-30
[COLOR="Red"]Mods: Feel free to lock or move to Recurring Discussions - it isn't my intent to start a OS war, just if anyone's noticed something similar[/COLOR]

I've just finished re-installing Feisty after another failed Gutsy install attempt. So, a new Feisty install from scratch.

And I've noticed something odd. My general performance metrics are better than my old benchmarks from yesterday prior to the abortive Gutsy installation, even though I install all the updates.

So... a fresh install runs better than an updated older install of the same OS? Windows XP SP2 behaves the same way, and often in tech forums there is a common recommendation to re-install the OS every so often.

The only reason that I can think of for this effect to happen is that even though various packages and files are updated, there is leftover older cruft from the older versions that are being referenced.

Yet, I thought that linux was based off files, so that things only referenced the files that they needed to. Is this not correct?

So, the question:

Have you noticed an improvement in performance after a re-install of the same system?

---

### Post by master5o1 on 2007-11-30
I prefer to reinstall every six months. It's much easier and saves on bandwidth cost (multiple computers, one cd download).

---

### Post by njparton on 2007-11-30
I guess it depends on whether you really are only updating your system or are actually adding additional stuff when you perform an update.

I definitely agree re the windows comment - 2 or 3 complete re-installs per year I average...

---

### Post by regomodo on 2007-11-30
i really can not tell the difference with linux. There may be a difference but it must be marginal.

Xp on the other hand is a whole different case

---

### Post by PrimoTurbo on 2007-11-30
When I did a update from Feisty to Gutsy my whole system became much slower, however when I did a clean install it was much faster.

---

### Post by p_quarles on 2007-11-30
My understanding is that the slowdown of a Windows system is due to filesystem fragmentation and registry dizziness. The first is easy -- but tedious -- to fix, and the second *can* be fixed -- also tedious -- if you know your way around the registry. 

The fragmentation experienced by an ext3 filesystem is negligible compared to NTFS, so that's not going to be a problem after just six months. So, my guess is that the upgrade slowness is more equivalent to registry conflicts -- you would get settings and services conflicts that the OS is capable of resolving without your intervention, but it slows the whole thing down.

I've never opted for the live upgrade, but I imagine that those issues could be fixed, and I imagine that they would also be tedious to fix.

---

### Post by popch on 2007-11-30
I think that could also be due to non-contiguous files on your disk. How do you defrag ext3?

---

### Post by p_quarles on 2007-11-30
> **popch said:**
> I think that could also be due to non-contiguous files on your disk. How do you defrag ext3?
From [Wikipedia]("http://en.wikipedia.org/wiki/Ext3"):
> 
**Defragmentation**

 There is no online ext3 [defragmentation]("http://en.wikipedia.org/wiki/Defragmentation") tool working on the filesystem level. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. But depending on the feature bits turned on the filesystem, e2defrag may destroy data; it does not know how to treat many of the newer ext3 features.[[4]]("http://en.wikipedia.org/wiki/Ext3#_note-3")

 There are userspace defragmentation tools like Shake[[2]]("http://vleu.net/shake/") and defrag[[3]]("http://ck.kolivas.org/apps/defrag/"), which work by copying each file and hoping the newly allocated file was not fragmented. However this only works if the filesystem is reasonably empty, and such filesystems are not usually fragmented. A true defragmentation tool does not exist for ext3 [[4]]("http://www.redhat.com/archives/ext3-users/2005-March/msg00013.html").

 However, as the Linux System Administrator Guide[[5]]("http://www.tldp.org/LDP/sag/html/filesystems.html") states, *"Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system."*

---

### Post by qazwsx on 2007-11-30
I quess it depends. If you keep your /home separated you ar ess likely to see any difference.  I prefer to use own  /home partition. I even share it with other distros (not so good practice) and that's why I have to clean some hidden /home stuff occasionally.

I have also noticed remarkable positve speed difference after I upgraded from edgy to feisty. I also experienced it with clean install (still the same old /home on different computer).

---

### Post by Scruffynerf on 2007-11-30
> **qazwsx said:**
> I quess it depends. If you keep your /home separated you ar ess likely to see any difference.  I prefer to use own  /home partition. I even share it with other distros (not so good practice) and that's why I have to clean some hidden /home stuff occasionally.

I have also noticed remarkable positve speed difference after I upgraded from edgy to feisty. I also experienced it with clean install (still the same old /home on different computer).

Interesting point, and for clarification, I run a separate home partition on a different physical drive.

---

