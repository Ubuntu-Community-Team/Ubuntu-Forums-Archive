---
title: "Simplifying partitions on backup drives"
date: 2020-01-06
forum: Server Platforms
---

### Post by aljames2 on 2020-01-06
How useful is Logical volumes (LVM) on backup HDDs:```
|ServerOS (on SSD)  -->   |internal spinning HDD#1 backup (w/5 logical partitions)  -->   |internal spinning HDD#2  (copy of HDD#1)  -->   |External spinning HDD#3 (copy of HDD#1)
[INDENT=6]-LnxData
-Shares
-Cloudy
-Websites
-Systems
[/INDENT]
```

For the HDD#1, there is in my case, 1 VG, & 5 LVs involved.  This is all within a LUKS container.  I like the LVs from a containment standpoint but I ask myself...why else?  Why LVs on backup drives.  It totally makes sense on Server OS's to contain directories, help with restores, etc.  I wonder if it's complexity worship on storage drives when 1 big static ext4 partition is tempting at times?  The additional drives have to be prepared with the same identical partitioning schemes (it seems) in order to maintain the structure & have true duplicates.  Is there a tool to copy over to the next drive the LVM scheme from the source drive?  If not, perhaps simplification with less LVs would be better.  One thing for sure, you get good at using Parted, fdisk, & LV command line tools...nothing wrong with that :)

---

### Post by TheFu on 2020-01-07
I don't think there is any single "right" answer.
I don't use complex LVM setups on my system backup disk.  All backups for each system get "pulled" by the backup server and stored inside the same LV.   For example:
```
$ tree -d -L 2 /Backups
/Backups 
&#9500;&#9472;&#9472; blog44
&#9474;** &#9500;&#9472;&#9472; etc
&#9474;** &#9500;&#9472;&#9472; home
&#9474;** &#9500;&#9472;&#9472; rdiff-backup-data
&#9474;** &#9500;&#9472;&#9472; root
&#9474;** &#9500;&#9472;&#9472; usr
&#9474;** &#9492;&#9472;&#9472; var
&#9500;&#9472;&#9472; cb35
&#9474;** &#9500;&#9472;&#9472; etc
&#9474;** &#9500;&#9472;&#9472; home
&#9474;** &#9500;&#9472;&#9472; rdiff-backup-data
&#9474;** &#9500;&#9472;&#9472; root
&#9474;** &#9500;&#9472;&#9472; usr
&#9474;** &#9492;&#9472;&#9472; var
&#9500;&#9472;&#9472; hadar
&#9474;** &#9500;&#9472;&#9472; etc
&#9474;** &#9500;&#9472;&#9472; home
&#9474;** &#9500;&#9472;&#9472; rdiff-backup-data
&#9474;** &#9500;&#9472;&#9472; root
&#9474;** &#9492;&#9472;&#9472; usr
&#9500;&#9472;&#9472; istar
&#9474;** &#9500;&#9472;&#9472; etc
&#9474;** &#9500;&#9472;&#9472; home
&#9474;** &#9500;&#9472;&#9472; rdiff-backup-data
&#9474;** &#9500;&#9472;&#9472; root
&#9474;** &#9500;&#9472;&#9472; usr
&#9474;** &#9492;&#9472;&#9472; var
&#9500;&#9472;&#9472; lubuntu
&#9474;** &#9500;&#9472;&#9472; etc
&#9474;** &#9500;&#9472;&#9472; home
&#9474;** &#9500;&#9472;&#9472; rdiff-backup-data
&#9474;** &#9500;&#9472;&#9472; root
&#9474;** &#9500;&#9472;&#9472; usr
&#9474;** &#9492;&#9472;&#9472; var
```
....
You get the idea.  These are daily, automatic, versioned, backups.  Each has at least 60 days, but some get 180 days of backups.  The /usr/ directories are really /usr/local/, not the stuff easily reinstalled.  rdiff-backup creates what appears to be a mirror for the latest backup with all older versions stored inside the rdiff-backup-data/ directory as diff.gz files.  It is very efficient and captures permission changes over time.  All the backups for the systems fit on a single 2TB disk.  That's a flaw, since when that disk fails, all the backups are gone. 

For media files, where I simply cannot afford to have daily, versioned, backups, the LVs on the backup disks mirror closely the LVs on the primary disks.

Anyway, that's what I do.  Really, the underlying storage doesn't need to be complicated. Simple is best, unless you need encrypted backups.  Accessing encrypted storage with LVM isn't very hard once you do it a few times. As with many things, practice and experience make it easier.

---

### Post by aljames2 on 2020-01-08
Makes sense, thanks TheFu

---

