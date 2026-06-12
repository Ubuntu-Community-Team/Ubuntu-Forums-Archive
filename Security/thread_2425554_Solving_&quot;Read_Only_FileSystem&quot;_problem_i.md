---
title: "Solving &quot;Read Only FileSystem&quot; problem in Ubuntu 19.04 which occurs once a week."
date: 2019-08-27
forum: Security
---

### Post by pranav.bhattarai on 2019-08-27
I alway keep my Laptop OSes update. I am a dual boot user (Windows 10 Pro & Ubuntu 1904).
Windows is as always had no problem but in Ubuntu I run into different kinds problem everyday. 

One big problem is FSCK and File System being Readonly.

How to maintain this distro? Did I made a wrong decision choosing a non-LTS version?
I really like to use non-LTS version because of features and speed improvemnt. Apart from this, this distro has always disappointed to me.

I have 64GB pendrive dedicated for this recurring issue. What i do is, I live boot 19.04 > Try without installing > Open Gparted > Select / and home partition leaving swap partition alone > Choose Check disk > Run.

This will solve the problem for a while and that's it. A week after, again the loop of "Read Only FileSystem and FSCK" circulates.

#SaveMe #EnlightenMe

---

### Post by TheFu on 2019-08-27
File systems get mounted read-only when there is corruption to it.  That should never happen.  EVER.

So you have some sort of issue, major issue, that will cause data loss.  It needs to be fixed.
Never just power off any Unix computer. Always shut it down. ALWAYS.

Never let Windows open any Linux file systems and not close them cleanly.  Windows likes to leave file systems open between "boots."

Check the SMART data for the storage device. I would use **smartctl**. Look at the raw data.  To my knowledge, the GUI tools don't show the raw data.

Check that the cabling to the storage is tight and can't become loose.

Using gparted seems like the hard way for something like running fsck.  I would just open a terminal and run fsck on the partition from the "Live Boot" environment.

File systems that have been around for 5+ yrs don't have corruption issues unless you are using them in a way they recommend against. If you are using ext4, there hasn't been any file corruption issues in released versions about 10 yrs. LTS or not, it doesn't matter.  If you are using BTRFS, there are some specific use cases which can be problematic.  Do some research to see if your use falls into the sort with issues.  For example, using BTRFS with virtual machines under some specific use-cases can be a problem.

---

