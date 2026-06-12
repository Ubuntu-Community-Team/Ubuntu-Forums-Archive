---
title: "Need masterplan for 16.04 on ZFS Root with Full Disk Encryption"
date: 2016-09-11
forum: Security
---

### Post by henrixd on 2016-09-11
My plan is to have a full disk encrypted system and local backup, both on different disks. My knowledge is very limited with ZFS and I'm hoping to get some good advices.

**Primary disk (I haven't bought it yet)**
OCZ TRION 150 2.5" 240GB SATA III TLC Internal Solid State Drive (SSD) TRN150-25SAT3-240G

This disk may not have the best endurance (~60Tb write) but it, hopefully, lasts long enough for me to get money for a better one. Since my CPU has AES-NI instruction set, I can save money by choosing a disk without built in encryption.

[B]Backup / Storage disk (Current primary disk)
[/B]Seagate 1TB SATA3 6.0Gb/s 3.5" 64MB Cache

Just some guides.
[http://www.makethenmakeinstall.com/2014/10/zfs-on-linux-with-luks-encrypted-disks/](http://www.makethenmakeinstall.com/2014/10/zfs-on-linux-with-luks-encrypted-disks/)
[https://github.com/zfsonlinux/zfs/wiki/Ubuntu-16.04-Root-on-ZFS](https://github.com/zfsonlinux/zfs/wiki/Ubuntu-16.04-Root-on-ZFS)

1. Raw disks (bottom)
2. LUKS encryption (zfs native encryption is coming, but not in time for this)[INDENT]aes-xts   256b  1807.6 MiB/s  1809.4 MiB/s
[/INDENT]
[INDENT]aes-xts   512b  1410.1 MiB/s  1351.8 MiB/s[/INDENT]
  3. ZFS Filesystem (top)

AES-XTS is the fastest choice on my system and as far as I know, it is secure enough for my purposes. ([http://crypto.stackexchange.com/questions/14628/why-do-we-use-xts-over-ctr-for-disk-encryption](http://crypto.stackexchange.com/questions/14628/why-do-we-use-xts-over-ctr-for-disk-encryption))

It is probably the best to have two single disk pools and use 'zfs send' for local backups because RAID mirror is not a backup and I don't want my SSD to be slowed down by HDD, correct?

What would you do, and why?

---

### Post by TheFu on 2016-09-12
Backblaze published statistics with 60K+ HDDs. [https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/](https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/)
Look at the seagate numbers carefully.

Versioned backups are critical. Don't know if using file system-based snapshots can provide 60 days of versioned backups. For a mirror, using remote snapshots like zsend provides makes perfect sense, but is that really all you want in a backup solution?

---

### Post by henrixd on 2016-09-12
Thank you for providing link to those numbers. That is something to think about. Seagate disks were the most used but failed a lot too. Their failure rate is little higher than what I would like to see. I would love to throw more disks into this, but I don't see it happening any time soon. It is unlikely for both drives fail at the same time, so that leaves me time to make a second backup if needed (I hope).

I'm not sure that I understand what's supposed to be wrong with ZFS snapshots. They seem to be the way to go based on googling 'ZFS backup'. "You can make many snapshots of a single ZFS filesystem (theoretically 2^64 in a storage pool) without any cost other than the disk space they consume, which is equal to the growth of your data (or rather; accumulated size of all changes) since the oldest snapshot." ([https://www.grendelman.net/wp/fast-frequent-incremental-zfs-backups-with-zrep/](https://www.grendelman.net/wp/fast-frequent-incremental-zfs-backups-with-zrep/))
They are easy to manage and are organized by date. However, there seem to exist a lot of all kind of backup solutions that I've been unaware of. I may have to look into this a little bit more too.

---

### Post by TheFu on 2016-09-12
Funny fonts don't help readability.

Snapshots stop the disk sectors from being modified, but doesn't get them to different physical media.  zsend does.  Most places that use snapshots use them to freeze the data long enough to make versioned backups to alternative storage, then remove those snapshots so the disk storage can be used for other purposes.  Places where I've worked that did use zfs always had tape backup and used snapshots just to stop the areas being backed up from changing. It is a well-worn methodology.

Regardless of what you select, be certain to test the restore.

Also, backups are slightly more secure if they are pulled, assuming the backup server is not accessible by the internet.

---

### Post by henrixd on 2016-09-12
Yeah, copy paste messed up those fonts and I somehow missed that.

You have a valid point and I will take that under consideration. Currently I just feel like the best place for a snapshot is another pool and that would make the managing just easier. I would still have two copies of the data in separate disks without any repeating blocks. I could send them back for rollback whenever I need to. This of course limits it to partitions and can not be made by per file basis. Other backup solutions have that and a few more features which I will need to look into.

This is exactly the kind of stuff I was hoping to get out from this. It is good that I have time to plan.

EDIT:
Alternatively I could leave Seagate disk unencrypted and backup files with 'Back In Time' or 'Déjà Dup' and use encryption with those.

---

