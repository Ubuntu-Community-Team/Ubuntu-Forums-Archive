---
title: "How a Linux Distro Saved Hard Disk Data"
date: 2005-11-08
forum: The Cafe
---

### Post by newbie2 on 2005-11-08
"Not too long ago, a friend sent me an e-mail that said, "I want to ask for a favor and see if you can help me to recover the data in the hard disk of my daughter's PC." I came to learn that some combination of utilities had wiped out the partition table in the master boot record (MBR). Maybe a tool such as fdisk could fix this problem, but the cylinder numbers weren't available. This article describes how, using a typical Linux distro (SuSE 8.0, in this case) it was possible to recover the master boot record and, with it, my friend's daughter's data."
[http://www.linuxjournal.com/article/8661](http://www.linuxjournal.com/article/8661)

---

### Post by kalin on 2005-11-08
There's a nice CLI tool in the "universe" repository, called testdisk. What it does is restore a harddisk's partition table out of nothing (it scans the HDD to find known filesystems).

I had to troubleshoot remotely a friend of mine in a similar situation (the MBR was all zeroes), what we did was:

1. boot from an Ubuntu live cd he had at hand
2. enable the universe repositories in synaptic
3. install testdisk
4. run testdisk in a terminal

Of course the computer was connected to the net in order to do that.

---

### Post by imagine on 2005-11-08
I had the same some weeks ago with a 200GB RAID 5 on a u320 SCSI-Controller, where the first sector got overwritten by zeros. Oh what a joy! Spent almost two days with this crap, since I'm not that familiar with deleted master boot sectors and partition tables... But in the end I got the data back.
I used testdisk too, but from a floppy : )

---

### Post by gray-squirrel on 2005-11-08
Great, another article from Linux Journal which shows how to recover data.  I've been looking around for some time after reading [How a Corrupted USB Drive Was Saved by GNU/Linux]("http://www.linuxjournal.com/article/8366") and trying to recover data off one of my flash drives.  It didn't work for me, because [FONT="Courier New"]fsck[/FONT] said that both FATs were corrupt.

I installed Sleuthkit and Autopsy about three weeks ago, and was so close to recovering files on the same disk image when I got an error message in Autopsy about something not being installed when it was.  I got sidetracked for a while and didn't get back to tracking down the problem.  Now I remember it after reading the article

Has anyone tried either solution (testdisk or [How a Linux Distro Saved Hard Disk Data]("http://www.linuxjournal.com/article/8661") on a flash drive (or its image) yet?  I'll try testdisk out first when I get home this evening, but I'm just curious as to how it went for you all and if there was anything I needed to be aware of when I try it.

---

