---
title: "Filesystem thread"
date: 2009-11-07
forum: The Cafe
---

### Post by ZankerH on 2009-11-07
So which do you use and why? Flame on! joking, kind of...

Myself, I'm still mostly using ext3, either because I never bother to do an clean install (case in point, my current ubuntu 9.10 install has seen a clean upgrade path from 7.10) or, in the case of my netbooks, because ext4 has been reported to severly reduce the lifetime of SSDs.

On a related note, I did, however, just wipe  a 1TB NTFS partition from a used disk I bought - the guy I bought it from didn't even bother to delete his files from it, and I'm sure I could have ruined his life if I bothered to just have a look around, but I'm not that evil. So which FS would you recommend for a 1TB partition that's mostly going to be used to store bulk data (plaintext logs, email archives,huge encryption keyfiles, etc) that only gets accessed once in a while?

---

### Post by SunnyRabbiera on 2009-11-07
I favor ext3 right now, will I use ext4?
Maybe once some bugs are fixed, its still new.
I hope btrfs lives up to expectations

---

### Post by Zoot7 on 2009-11-07
I'm using ext4 wherever I can. :)

I'm slowly moving my external and internal storage hard drives to either ext3 or ext4 from ntfs, merely for the reason that I saw an ntfs filesystem get totally corrupted for no real reason about 2 months ago. It's a slow process, because there's nearly 7 terabytes there, only half way there yet. :biggrin:

[QUOTE=ZankerH]So which FS would you recommend for a 1TB partition that's mostly going to be used to store bulk data (plaintext logs, email archives,huge encryption keyfiles, etc) that only gets accessed once in a while?[/QUOTE]
It depends on which OS you want to access the partition. If it's Linux only i'd go with ext3.

---

### Post by SuperSonic4 on 2009-11-07
**_System_**

/     = ext4
/home = ext4
/var  = reiserfs


**_Media_**

/mnt/Documents = ext4
/mnt/Videos    = jfs
/mnt/Music     = xfs
/mnt/Pictures  = ext4

---

### Post by ZankerH on 2009-11-07
> It depends on which OS you want to access the partition. If it's Linux only i'd go with ext3.

I'll be accessing it locally with GNU/Linux and FreeBSD, anything else will only see it through sshfs.

---

### Post by cariboo on 2009-11-07
All linux based systems but my server use ext4, the / partition on the server is ext4 all the others including an external are xfs. I've also got a dual boot laptop ntfs/ext4 and two windows systems ntfs

---

### Post by Dark Aspect on 2009-11-07
ext3 since I am worried about my huge collection of flac audio on ext4 that would take me 4 years to rip again from all of the cds. Some of my audio cds I no longer have the original to.

---

### Post by blueshiftoverwatch on 2009-11-07
I'm using ext4 because although I would hate to have to loose information I keep all of my important data backed up on an external hard drive. So I might as wells suck it up and live dangerously.

---

### Post by schauerlich on 2009-11-07
HFS+


a

---

### Post by Regenweald on 2009-11-07
Ext4 now, all partitions and when BTrFS is available on  install, then that.

---

### Post by RiceMonster on 2009-11-07
Ext4 on my laptop and desktop. External HD is NTFS so I can use it with windows no problem.

---

### Post by kyuubi777 on 2009-11-07
Ext4 on my laptop for all three of my distros on it.

---

### Post by fela on 2009-11-07
ext4 on my desktop; ext3 on my server.

---

### Post by kk0sse54 on 2009-11-07
**FreeBSD** ZFS
**Arch** JFS
**External HD** NTFS

---

### Post by tom66 on 2009-11-07
See screenshot.

"Unknown" appears to be corrupted swap partition. I'm unsure. But Ubuntu has so far no need for a swap as it's got 3 gigabytes of RAM. 

/windows has Windows Vista SP1 on it, which is rarely used.

I also have about 3 versions of Ubuntu on here and a version of Arch somewhere.

All my USB/external drives use NTFS, for interoperability with many Windows systems which don't have ext2/3/4 filesystem drivers.

---

### Post by schauerlich on 2009-11-07
> **tom66 said:**
> See screenshot.

Holy partitions, batman!

---

### Post by DoktorSeven on 2009-11-07
ext3.  Not changing to ext4 for a loooooooooonnnng time.  Filesystems have to be completely rock solid for me, and even though ext4 has gotten past its growing pains, I still don't 100% trust it... yet.

---

### Post by Dark Aspect on 2009-11-08
> **DoktorSeven said:**
> ext3.  Not changing to ext4 for a loooooooooonnnng time.  Filesystems have to be completely rock solid for me, and even though ext4 has gotten past its growing pains, I still don't 100% trust it... yet.

+1

I can't justify trusting my data with something like ext4 the same way I don't trust Microsoft for every day computer activities. Also, eating files above 500 MBs sounds like a growing pain to me; reminds me of alpha/beta software.

---

### Post by FuturePilot on 2009-11-08
See screenshots

---

### Post by gnomeuser on 2009-11-08
/ on btrfs 

(with a separate /boot on ext4 due to a current lack of btrfs support in bootloaders though as always patches are available).

It is treating me well

---

### Post by infestor on 2009-11-08
ext4 & ntfs (from old times, too lazy to format)
i guess rather than ext3 or ext4 for an average PC user is unnecessary.

---

### Post by praveesh on 2009-11-08
Iam using xfs . When I installed Ubuntu in a xfs partition , it became much faster than in ext3 . I tried using ext4 but didn't feel much performance improvement in Ubuntu (ie responsiveness and program loading speed). So I switched to xfs

---

### Post by bobtestact on 2009-11-08
In the release notes, there was a concern about corruption in ext4 when writing to large files (over 512MB).  See:

[http://www.ubuntu.com/getubuntu/releasenotes/910#Possible%20corruption%20of%20large%20files%20with%20ext4%20filesystem](http://www.ubuntu.com/getubuntu/releasenotes/910#Possible%20corruption%20of%20large%20files%20with%20ext4%20filesystem)

From what I can tell, the investigation seems to be stuck on trying to reproduce the problem, and I have not seen a confirmed report of this problem on the forums.

The fact that ext4 is the default in 9.10 on new partitions means that ext4 has probably been given quite an extensive workout during the past week.  If it's really true that no new reports are surfacing of the 512MB+ corruption bug, do you think it's safe to stop worrying about this issue when deciding between ext3 and ext4?

---

### Post by blueshiftoverwatch on 2009-11-08
How much faster is ext4 than ext3?

---

