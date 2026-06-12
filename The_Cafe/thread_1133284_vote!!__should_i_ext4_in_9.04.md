---
title: "vote!!  should i ext4 in 9.04?"
date: 2009-04-22
forum: The Cafe
---

### Post by northwestuntu on 2009-04-22
im going back and forth about using ext4 with a fresh install of 9.04.  i've read where people have had problems and other people had no problems.  i've heard it's faster and i have heard it's not faster :confused:

so based on this vote will either install ext3 or ext4.

in fact most of my decisions in life will be based on ubuntuforums.org votes from now on :)

---

### Post by SomeGuyDude on 2009-04-22
I've been using ext4 on an Arch64 install for a few weeks now and it's phenomenal. WAY better than the XFS I'd been using previously.

---

### Post by Bölvaður on 2009-04-22
There are problems with ext4, see the release notes (problem section of it) about what is wrong with it. ext3 just to be sure.

---

### Post by northwestuntu on 2009-04-22
> **Bölvaður said:**
> There are problems with ext4, see the release notes (problem section of it) about what is wrong with it. ext3 just to be sure.


yeah i did just see this now that you mentioned the release notes

Lock-ups when deleting files from ext4 filesystems

In some cases, deleting files from an ext4 filesystem is reported to cause soft lock-ups in the kernel (330824). Investigation of this problem is ongoing, and it is expected that a fix for this problem will be made available as a post-release update. To avoid this problem, users may wish to install using the default ext3 filesystem and convert their filesystem to ext4 (as documented on the ext4 wiki) once a fix is available.

---

### Post by gnomeuser on 2009-04-22
Ext4 has treated me very well for the past year. I say go for it.

---

### Post by Simian Man on 2009-04-22
I too have been using ext4 for months without any problems (on Fedora).  I say go for it :).

---

### Post by Sealbhach on 2009-04-22
Have had no probs with ext4 for the last month on Jaunty. But yes, there are some risks still, particularly data loss in the event of a sudden shutdown, if I understand correctly.


.

---

### Post by gnomeuser on 2009-04-22
> **Sealbhach said:**
> Have had no probs with ext4 for the last month on Jaunty. But yes, there are some risks still, particularly data loss in the event of a sudden shutdown, if I understand correctly.


.

The behaviour has now been changed to be more like ext3 till such a time as applications get fixed.

Aside that anytime you pull the system out from underneath a program you risk dataloss, the question is more about what we guarantee in that case. It should be a file or no file situation, not a file with the wrong stuff in it or an empty file.

---

### Post by wolfen69 on 2009-04-22
> **northwestuntu said:**
> 
Lock-ups when deleting files from ext4 filesystems


i've deleted many big files without issue. been using it for over a month now. i would not worry about it.

---

### Post by smartboyathome on 2009-04-22
Just for everyone not on Ubuntu (it is fixed on Ubuntu by default), add rootflags=data=ordered to your kernel line in /boot/grub/menu.lst to make sure that you don't lose data when you have to hard shutdown. Other than that, it has been treating me great! :)

---

### Post by reprobus on 2009-04-22
I'm running the Jaunty release candidate and ext4 has worked fine for me so far.

---

### Post by rileinc on 2009-04-22
How significant will data loss or soft lock ups affect you? If the answer is "very," you should stick with ext3.

I save everything on separate NTFS hard drives to make them accessible on Windows (dual boot). Only temporary files are saved in /Home (ext3). 
For me, a data loss is neither likely nor serious. That is why I'll be using ext4 for Jaunty.

---

### Post by Skripka on 2009-04-22
> **northwestuntu said:**
> im going back and forth about using ext4 with a fresh install of 9.04.  i've read where people have had problems and other people had no problems.  i've heard it's faster and i have heard it's not faster :confused:

so based on this vote will either install ext3 or ext4.

in fact most of my decisions in life will be based on ubuntuforums.org votes from now on :)

Fsck is FAR faster.  My 250GB drive used to take about 5 minutes to fsck on Ext3.  The same drive on Ext4 can be fsck'd in less thaan 30 seconds.

Per Smartboyathome, edit your menu.lst as told and you should be fine regarding data corruption/loss duing hard poweroff/reboot.

---

### Post by FuturePilot on 2009-04-22
I actually went back to Ext3 on my main machine because there is a big show stopping for me [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824")

If you care about your data and stability I would recommend sticking with Ext3 for a bit longer.

---

### Post by northwestuntu on 2009-04-22
> **FuturePilot said:**
> I actually went back to Ext3 on my main machine because there is a big show stopping for me [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824")

If you care about your data and stability I would recommend sticking with Ext3 for a bit longer.

isn't that the bug they just fixed?

---

### Post by FuturePilot on 2009-04-22
> **northwestuntu said:**
> isn't that the bug they just fixed?

No, it's not fixed. I think you're thinking of the data loss bug. This is different.

---

### Post by penguindrive on 2009-04-22
EXT4, Its just plain better.

---

### Post by wolfen69 on 2009-04-22
> **Skripka said:**
> Fsck is FAR faster.  My 250GB drive used to take about 5 minutes to fsck on Ext3.  The same drive on Ext4 can be fsck'd in less thaan 30 seconds.


mine went from 90 seconds to 7 seconds. not bad.
> **penguindrive said:**
> EXT4, Its just plain better.
yeah, i will never go back to ext3 or 32bit.(except in a VM) ext4 and 64bit are the way to go if you want performance. besides, i keep all my important stuff on other drives. (backed up 3 times in total, i don't take any chances.) but so far i havn't seen any of the problems people speak of.

---

### Post by 71CH on 2009-04-22
What's so great about ext4?

---

### Post by SomeGuyDude on 2009-04-23
Speed, mostly.

The biggest difference I noticed was moving around and deleting large amounts of files. I tend to back-up my crap a lot and moving, say, 20 gigs of MP3 was an AGONIZING undertaking with ext3 and XFS, and it's dang snappy with ext4.

---

