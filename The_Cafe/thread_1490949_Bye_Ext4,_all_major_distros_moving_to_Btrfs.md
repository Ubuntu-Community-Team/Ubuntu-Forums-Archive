---
title: "Bye Ext4, all major distros moving to Btrfs"
date: 2010-05-23
forum: The Cafe
---

### Post by madjr on 2010-05-23
> Fedora was the first tier-one Linux distribution shipping with support for optionally installing to a Btrfs file-system for the past year, but in recent weeks the adoption rate of Btrfs looks like it will be quickly rising. Fedora 13 is extending the Btrfs support to offer system rollback support  by where a file-system snapshot is created via Btrfs each time a yum transaction takes place. Red Hat recently released the first public beta of Red Hat Enterprise Linux 6.0 and it includes Ananconda installation support for RHEL6 onto Btrfs, MeeGo will be using Btrfs by default in this distribution that marries Maemo and Moblin, and Ubuntu is making Btrfs plans where Btrfs may become the default file-system in Ubuntu 10.10. Novell / openSUSE is also getting in bed with Btrfs.

Being worked on for openSUSE 11.3, which is due for release in July, is snapshot/rollback support for Btrfs in a similar fashion to Red Hat's implementation with Fedora 13. A Novell customer is pushing for this capability whereby a Btrfs copy-on-write snapshot is created by libzypp / zypper before a commit happens that changes a package's state. There would then be an exposed interface to revert to an earlier snapshot should something go awry.

........


Full details:
[http://www.phoronix.com/scan.php?page=news_item&px=ODI2Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODI2Ng)

---

### Post by CharlesA on 2010-05-23
Damn, just when I moved my server over to ext4...

---

### Post by Ozymandias_117 on 2010-05-23
I'm just wondering if the snapshots will take up much hard drive space, not really clear on how it works. Could be an awesome idea though, make a full install like a Virtual Machine being able to test things and revert easily.

---

### Post by toupeiro on 2010-05-23
If they're anything like WAFL snapshots, they will be point in time captures of the filesystem in which differential change is captured until the next snapshot, thus its not "imaging" or "cloning" but truly a stateful filesystem "state" of time.  This, of course, has its advantages and disadvantages.  Deletes... are no longer *really* deletes until your snapshots are purged.  When used right, they can be EXTREMELY useful.  When used wrong, they can be very counter-productive.

---

### Post by Ozymandias_117 on 2010-05-23
> **toupeiro said:**
> If they're anything like WAFL snapshots, they will be point in time captures of the filesystem in which differential change is captured until the next snapshot, thus its not "imaging" or "cloning" but truly a stateful filesystem "state" of time.  This, of course, has its advantages and disadvantages.  Deletes... are no longer *really* deletes until your snapshots are purged.  When used right, they can be EXTREMELY useful.  When used wrong, they can be very counter-productive.

Wouldn't this mean that deleting, even rm, would be like a trash can? It would remain until you purge the snapshot, still taking up hard drive space?

---

### Post by madjr on 2010-05-23
> **Ozymandias_117 said:**
> Wouldn't this mean that deleting, even rm, would be like a trash can? It would remain until you purge the snapshot, still taking up hard drive space?

is similar to Zfs and timeslider (opensolaris)


here's a vid showing time slider in action
[http://www.youtube.com/watch?v=jfCtqX8dQtk&feature=related](http://www.youtube.com/watch?v=jfCtqX8dQtk&feature=related)

---

### Post by Supergoo on 2010-05-23
I will have to read more on this file system, I Always liked and still Like the ZFS file system. Thanks for the infomation looking forward to digging through it.

---

### Post by madjr on 2010-05-24
> **Supergoo said:**
> I will have to read more on this file system, I Always liked and still Like the ZFS file system. Thanks for the infomation looking forward to digging through it.

zfs is good but the license was a problem.

weird how they first were competitors, now the same company devs them

---

### Post by trallen on 2010-06-14
> **CharlesA said:**
> Damn, just when I moved my server over to ext4...

[https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3]("https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3")

You can do an in-place conversion which (in theory) is completely safe as you can always roll back to the original ext[34] filesystem via btrfs's snapshot of the original ext[34] fs.

---

### Post by NightwishFan on 2010-06-14
I doubt btrfs will be the default in the next Ubuntu release. I probably will not be using it for a while either.

---

### Post by ubunterooster on 2010-06-14
> **Ozymandias_117 said:**
> Wouldn't this mean that deleting, even rm, would be like a trash can? It would remain until you purge the snapshot, still taking up hard drive space?
Sounds bad for SSDs

---

### Post by szymon_g on 2010-06-14
I wonder when it will be stable and usable... i hope they will test it more than they tested ext4 (i.e- no semi-working semi-stable solutions marked as stable so people could test them 'in field')

---

### Post by Shining Arcanine on 2010-06-14
> **madjr said:**
> Full details:
[http://www.phoronix.com/scan.php?page=news_item&px=ODI2Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODI2Ng)
I think the article is misleading because I believe that Gentoo Linux had Btrfs available before any other major distribution. :/

---

