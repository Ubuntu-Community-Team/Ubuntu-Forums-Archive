---
title: "Does Ubuntu run better on hard drive with bad sectors than any other OS"
date: 2016-08-27
forum: Windows
---

### Post by tech291083 on 2016-08-27
Hi Friends,

I have used both Windows and Ubuntu for a number of years now, but somehow I have got a feeling that whenever I check for bad sectors on a hard drive running Windows only - using the in-built app named "Disks" on Ubuntu DVD (I try Ubuntu and not install from DVD to check for bad sectors if any), and if I happen to find any bad sectors, then I just stop using that hard drive and install Ubuntu on it, this has been a tradition with me now, and the reason being the fact that the same hard drive with bad sectors tends to crash while running Windows more often than running Ubuntu. 

I am no expert on storage devices or Ubuntu's own underlying architecture, but Ubuntu has always impressed by running more efficiently than Windows on hard drives with bad sectors, do you happen to have the same view? I am not blaming Windows or any other OS, but if there is any truth in this, then I would love to know the real technical reason behind it if any, thanks a lot.

---

### Post by TheFu on 2016-08-27
To be fair, I bet that many unexplained crashes in these forums are due to storage issues.  

All spinning disks have "bit rot" ... where the bits were written a few years ago and don't get refreshed often enough to refresh the magnetic levels.  Eventually, this will lead to read failures. I suspect that parts of Windows don't get refreshed as often as similar parts in Linux, so Windows is more likely to display those problems.  If folks would just read + write the files every 6 months on all their disks, then the drive firmware would get a chance to see failing disk areas and move that data to spare blocks (which all HDDs have). This would also refesh the magnetics for files that are starting to have weak magnetics. So it really is just a use difference, not that Linux is a better OS for this reason (even if I believe it is a better OS for many other reasons). ;)  Refreshing the files and exercising the HDD storage is what makes this not happen on Linux.

That's my guess.

There are tools which do all of these things for every OS.  On Linux, we tend to make backups more often and restore those. Plus people tend to move to a new release every 2 years at the longest (LTS types, like me).  This effectively re-writes the data on disk, refreshing all those bits.  On Windows, most home users do not backup anything but a few files via something like drop-box. The OS gets patched, but how often do the core libraries/DLLs and kernel get swapped out in Windows? Every 4+ yrs? That's too long.

---

### Post by tech291083 on 2016-09-04
> **TheFu said:**
> 
I suspect that parts of Windows don't get refreshed as often as similar parts in Linux, so Windows is more likely to display those problems.  

Plus people tend to move to a new release every 2 years at the longest.

  This effectively re-writes the data on disk, refreshing all those bits.  On Windows, most home users do not backup anything but a few files via something like drop-box. The OS gets patched, but how often do the core libraries/DLLs and kernel get swapped out in Windows? Every 4+ yrs? That's too long.


This is really an interesting point you have made. If I understand correctly, Linux goes through a major change in its code base/architecture and that too faster than Windows, thus Ubuntu might tend to run better than Windows on old drives with bad sectors, right? I appreciate your understanding of the science of hard disks.

Thanks.

---

### Post by TheFu on 2016-09-04
No architecture changes - at least not many - with Unix/Linux. It is simply that most people reload their OS completely every few years so the bits get refreshed at least that often.  

Not a Windows or Linux or BSD or OSX thing. Purely a HDD getting refreshed thing.  If people did backups and restores that often, the problem wouldn't exist either.

---

### Post by tech291083 on 2016-09-04
> **TheFu said:**
> 
Purely a HDD getting refreshed thing.  If people did backups and restores that often, the problem wouldn't exist either.


OK, makes sense now, thanks a lot.

---

### Post by mörgæs on 2016-09-04
There could be other explanations. Neither am I an expert on the field but maybe ext4 is a more robust file system than NTFS.

Also a typical Buntu installation is much smaller than a typical Windows. Less sectors in use on the hard disk = less risk of encountering a dodgy one.

---

### Post by tech291083 on 2016-09-06
> **mörgæs said:**
> 
 maybe ext4 is a more robust file system than NTFS.


I am too not sure, but if this is a fact, then its a great news. Thanks.

---

### Post by 6975 on 2016-09-08
Let me make it clear then from my old direct experiences.
1. Run Linux doesn't make you safer from Windows against bad sector. 
    Once the hdd can't boot it's unusable unable to boot any OS
2. Ubuntu alert error clearly a lot from Gnome disk bad sectors or hdd that nearly RIP. 
    But windows they don't alert anything unless you install HD tune, CrystalMark to check the bad sectors.

---

### Post by tech291083 on 2016-09-13
Thanks.

---

