---
title: "Mirror between partitons and disk [ubuntu server]"
date: 2017-04-16
forum: Server Platforms
---

### Post by sed_faster on 2017-04-16
Hello follks,

I have a ubuntu server with this drives:

55GB
74GB (system)
153GB
74GB

I intend build two partitions on the drive (153GB). Because I want two drives and three partitions with 74GB each one. The goal is have this structure: 

System: 74GB
Backups: 153GB -> Partitions1(76GB) -> Partitions2(76GB)
Data1: (55GB)
Data2: (74GB)

My goal is create a mirror system! As I don't know how create this system through board(bios) I am trying build this solution from system (ubuntu server).
How should I configure the system to each times I shutdown the system the process of the turn off run the script, for example, to copy all data the data1 and data2 to partitions1 and partitions2, respectively. 
The process should be incremental. And to do this I am thinking use the program: sync, I think it will be a good idea!

What do you think about this?
Thanks

---

### Post by TheFu on 2017-04-16
I would use an incremental, versioned, backup tool for this - something like rdiff-backup.  A simple mirror is NOT sufficient for backups.  60 days of backup versions is pretty easy and not much more storage. You'd be surprised.  On my high-risk systems, I keep 120 days over versioned backups. 

If you want a RAID1 setup (which is a mirror, without any versioning), then use **mdadm** and Linux software RAID. I've never come up with a good reason to use the motherboard RAID capabilities - ever. There are many, many, many, reasons to avoid that method.

---

### Post by SuperFreak on 2017-04-16
I don't see much point in running RAID on the same disk with two partitions. If the disk fails both partitions are gone. Better RAID on two separate disks.
But I agree with TheFu, backups are the best idea. I keep multiple backups with at least one off site and rotate the disks between locations

---

### Post by sed_faster on 2017-04-17
Hello folks,

When I read about version control and backup tool my mouth drew a smile :) To some directories I was use git, but the repository was bigger and the git don't handle to amount data, like, more a less 10 GB. Recently I was study about git lfs ([https://git-lfs.github.com/](https://git-lfs.github.com/)), but to create this environment I need more experience with git, when I try build the a solution with this program I received some error which I can't handle very well.

Once time which I lost the process to handle data and ensure which I will have the same data across multiple pc I built a server with ubuntu server. The purpose of this server it is provide a local where I can put my data and ensure which I will use a version.

I was reading about rdiff-backup, ([http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html)). At the moment I still can't understand and create a environment with this but, more later I will read more deeply about this program. But if you have any testimony or article which you want share I will appreciate read about this :)

Thanks

---

### Post by TheFu on 2017-04-17
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) has the best article on rdiff-backup that I've seen.

---

