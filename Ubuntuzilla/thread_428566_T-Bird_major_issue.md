---
title: "T-Bird major issue"
date: 2007-04-30
forum: Ubuntuzilla
---

### Post by shane2peru on 2007-04-30
Ok, I installed TBird using the script.  I didn't have it installed.  However in the past two days of running it, I had one serious crash in that was unrecoverable.  They system hung up and refused to respond.  I had tried to send an email and it didn't go (Thunderbird had been open for quite some time in the background, just running quietly).  Not even ctrl-alt-backspace did the trick had to hold the power button to kill everything.  Today after Thunderbird was open for a few hours in the background, everything got terrible slow I mean the mouse didn't even respond quickly.  After about 30 minutes of sloooooow work, I was able to get alt-f2 to respond and killed mozilla-thunderbird-bin after about 30 seconds everything was running smoothly again.  The only changes I have made is1.  Installed ThunderBird  2.  Got OOO quickstart to startup and stay in the taskbar.  So I'm linking this problem to Thunderbird.  Going to uninstall and install the package in the repos to confirm if this is an outside package problem, or another problem on my system.  Wanted to post it here in case anyone else is experiencing this problem.

Shane

---

### Post by shane2peru on 2007-04-30
> **shane2peru said:**
> Ok, I installed TBird using the script.  I didn't have it installed.  However in the past two days of running it, I had one serious crash in that was unrecoverable.  They system hung up and refused to respond.  I had tried to send an email and it didn't go (Thunderbird had been open for quite some time in the background, just running quietly).  Not even ctrl-alt-backspace did the trick had to hold the power button to kill everything.  Today after Thunderbird was open for a few hours in the background, everything got terrible slow I mean the mouse didn't even respond quickly.  After about 30 minutes of sloooooow work, I was able to get alt-f2 to respond and killed mozilla-thunderbird-bin after about 30 seconds everything was running smoothly again.  The only changes I have made is1.  Installed ThunderBird  2.  Got OOO quickstart to startup and stay in the taskbar.  So I'm linking this problem to Thunderbird.  Going to uninstall and install the package in the repos to confirm if this is an outside package problem, or another problem on my system.  Wanted to post it here in case anyone else is experiencing this problem.

Shane

**Edit**  Ok, this is not good.  I just found out that only version 1.5 is in the repos and this script installed version 2, so now all my info is not available.  HELP.  This is not good.  I know, I should have read the stickies before.  I guess I will re-install the script and just not leave T-Bird running very long.  This is a slight problem.  :)

**Edit:** I meant to edit the last post, not quote myself.  :)

---

### Post by nanotube on 2007-04-30
mm, well, this would be a very difficult problem to troubleshoot... 
you're the first to report this, and i personally have been running tb2, as installed by the script, without any issues. 
try various things, like compacting all your folders, removing automatic email checking (see if it's maybe one of your mail servers that is having issues and giving TB problems)...

---

### Post by shane2peru on 2007-04-30
> **nanotube said:**
> mm, well, this would be a very difficult problem to troubleshoot... 
you're the first to report this, and i personally have been running tb2, as installed by the script, without any issues. 
try various things, like compacting all your folders, removing automatic email checking (see if it's maybe one of your mail servers that is having issues and giving TB problems)...

Ok, I'm wondering now if this is a fluke, and the problem wasn't TB.  I also had a hang up with FireFox running.  I'm wondering if it isn't 1.  The Quickstart thing for OOO (I disabled it)  or 2.  Beagle  Either way I have no real way of troubleshooting short of trial and error.  I guess that is what I will have to do. It is looking like it isn't TB after all, sorry for the false alarm.  It is also good to know that you have run this a while and not had problems with it.  Thanks for the info.

Shane

---

### Post by nanotube on 2007-04-30
> **shane2peru said:**
> Ok, I'm wondering now if this is a fluke, and the problem wasn't TB.  I also had a hang up with FireFox running.  I'm wondering if it isn't 1.  The Quickstart thing for OOO (I disabled it)  or 2.  Beagle  Either way I have no real way of troubleshooting short of trial and error.  I guess that is what I will have to do. It is looking like it isn't TB after all, sorry for the false alarm.  It is also good to know that you have run this a while and not had problems with it.  Thanks for the info.

Shane

ok, well, please post back here if you do end up figuring out what it was. :)

---

### Post by shane2peru on 2007-04-30
> **nanotube said:**
> ok, well, please post back here if you do end up figuring out what it was. :)

Will do.  I'm thinking that it is Beagle giving me problems.  I started the daemon, and it really brought my computer to a crawling speed.  

Shane

---

### Post by shane2peru on 2007-05-01
Ok, the issue seems as though it was my swap was not mounted.  At least that is what happened to me today same issue.  Did a dmesg tail thing, and it showed I had no swap space left.  I checked with gparted and swap was not mounted.  I mounted it, but I'm not sure why it wasn't mounted, and how I can keep that from happening again.

Shane

---

### Post by nanotube on 2007-05-01
> **shane2peru said:**
> Ok, the issue seems as though it was my swap was not mounted.  At least that is what happened to me today same issue.  Did a dmesg tail thing, and it showed I had no swap space left.  I checked with gparted and swap was not mounted.  I mounted it, but I'm not sure why it wasn't mounted, and how I can keep that from happening again.

Shane

well, is it listed in your /etc/fstab?

---

### Post by shane2peru on 2007-05-02
> **nanotube said:**
> well, is it listed in your /etc/fstab?

# /dev/sda3
UUID=366a229d-bf5b-4292-96ae-261ec4f8c9d9 none            swap    sw 

This is from my fstab, so it is there.  Do you know how I list the UUID number to see if it is correct?  I don't quite understand this UUID number stuff, and am not really convinced it is better.

Shane

---

### Post by nanotube on 2007-05-02
> **shane2peru said:**
> # /dev/sda3
UUID=366a229d-bf5b-4292-96ae-261ec4f8c9d9 none            swap    sw 

This is from my fstab, so it is there.  Do you know how I list the UUID number to see if it is correct?  I don't quite understand this UUID number stuff, and am not really convinced it is better.

Shane

no, i don't know anything about uuid numbers... why don't you just try using the /dev/whatever instead, and see if that helps?

first, run
```
sudo fdisk -l
Password:

Disk /dev/hdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            2494        4863    19037025    f  W95 Ext'd (LBA)
/dev/hdc3            1276        2493     9783585   83  Linux
/dev/hdc5            2551        4863    18579141    c  W95 FAT32 (LBA)
/dev/hdc6            2494        2550      457789+  82  Linux swap / Solaris

```

notice in the output one of the partitions says "linux swap" - that's the one you want. for me, it's hdc6. so then you would make your fstab line look like:
```
/dev/hdc6       none            swap    sw              0       0
```

try that...

---

### Post by shane2peru on 2007-05-02
> **nanotube said:**
> no, i don't know anything about uuid numbers... why don't you just try using the /dev/whatever instead, and see if that helps?

first, run
```
sudo fdisk -l
Password:

Disk /dev/hdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            2494        4863    19037025    f  W95 Ext'd (LBA)
/dev/hdc3            1276        2493     9783585   83  Linux
/dev/hdc5            2551        4863    18579141    c  W95 FAT32 (LBA)
/dev/hdc6            2494        2550      457789+  82  Linux swap / Solaris

```

notice in the output one of the partitions says "linux swap" - that's the one you want. for me, it's hdc6. so then you would make your fstab line look like:
```
/dev/hdc6       none            swap    sw              0       0
```

try that...

OK, did that, and that seemed to fix things.  Thanks.

Shane

---

### Post by nanotube on 2007-05-02
> **shane2peru said:**
> OK, did that, and that seemed to fix things.  Thanks.

Shane

cool. :)

---

