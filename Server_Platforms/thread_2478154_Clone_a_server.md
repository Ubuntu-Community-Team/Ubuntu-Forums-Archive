---
title: "Clone a server"
date: 2022-08-18
forum: Server Platforms
---

### Post by blondie63 on 2022-08-18
I have an Ubuntu 18.04 server at a cloud provider that doesn't allow backup downloads
I would like to clone it somehow and then install it locally on my VMware host
I have root access!

Some idea ?

Thank you

---

### Post by LHammonds on 2022-08-18
Well, if the ISP does not allow access to the tools to do this, your next bet would be internal tools of the operating system itself.

I would install another server elsewhere and configure both for connectivity to each other and copy the configurations / data from one server to the other.  This requires firewall rules and Internet connectivity.

scp can copy files/folders from one server to another server via SSH.
You could setup a VPN between them.
You could use something like WinSCP to download files to your PC, then upload them to another server.

If the whole point of cloning is due to you not knowing how to configure a new server to work like the old one, then you might want to invest some time in figuring out how to install a new server to work like the old one.  Preferably using a newer OS version such as 22.04.

Another potential solution if you have the space is to use fsarchiver to create a backup of a partition to a file on the OS...then transfer off that backup using file transfer methods such as the ones mentioned above...but there are many ways to skin that cat....all depends on your environment, configuration, skill level, etc.

LHammonds

---

### Post by blondie63 on 2022-08-18
In this server i've 5 docker containers to serve a webapp, i don't think that a file copy is possible when webapp is running!
Now i've commit and saved all containers and i'm moving to new server
When i finish i'll try to load and run them :)
I was hoping to find a way to image the entire server from the inside with some scripts to a remote server via ssh. A bit like VMware Converter did with the P2V function

---

### Post by LHammonds on 2022-08-20
I do not use Docker so I cannot comment directly about that.

The only thing that I have done that matches what you say is the use of fsarchiver to make online snapshots of the various partitions and use those to restore on another machine.  This of course is not an instant-on solution and if you have a service that is online all of the time, it will just get you a clone of your production server at a snapshot at a prior point in time (however long it takes to make the partition backup, transfer and restore.  If you need to capture data since the time of backup and the time when the clone is ready to replace the other, you will need to work out the details of the apps for app-level backup/restore...assuming you cannot have the service down during the backup/restore process.

Keep in mind that I configured my servers from scratch to ensure I could create a partition-level backup using LVM.   I have backups at the data level (scheduled often via scripts), VM level (scheduled daily via enterprise-level backup software) and at the partition level (scheduled monthly on the OS with fsarchiver).  My data and partition backups are pulled off the servers by a remote backup server and the daily backups are done at the VM level at a remote data center.  I have at least 2 different ways to restore (or clone) individual files or the entire server.

I've documented [how I use fsarchiver to backup a server](https://hammondslegacy.com/forum/viewtopic.php?p=1022#p1022) and [how to restore](https://hammondslegacy.com/forum/viewtopic.php?p=1023#p1023).  But this may not be an option for you if your server was not designed for this type of operation.  For example, if you configured your server to use a single large partition and left no unused space, this is not really an option you can use.

LHammonds

---

### Post by bad-nixguy on 2022-08-22
i. You can use dd cmd to store whole drive to a single .iso file. Then using scp cmd copy it over to your local PC/laptop. Depends on virtualization s/w you'll use I assume you can create hdd-style file (or create a VM with new hdd file), attach it to existing linux VM of any kind/version and use restore cmd to unpack .iso file to needed hdd. Last step - attach that hdd back to new VM and run it. Btw hdd disk size should be >= origin. If you will do > you will have some free non allocated space on a new hdd and if you want to extend main partition to use that free space - another software can help you. But it's another story.

ii. More dirty way but still:

On Cloud server do something like this:
1. sudo tar cjvf all.tar.bz2 /* (create an archive with whatever system can give you access to)
Install the same Ubuntu ver. on VM, copy over archive and do this:
2. sudo tar xjvPf all.tar.bz2
Maybe for the second step it's a good idea to connect target hdd to another VM and do "tar xjvPf all.tar.bz2" there.

---

### Post by blondie63 on 2022-08-22
oki i'll try thanks

---

### Post by TheFu on 2022-08-22
> **blondie63 said:**
> In this server i've 5 docker containers to serve a webapp, i don't think that a file copy is possible when webapp is running!
Now i've commit and saved all containers and i'm moving to new server
When i finish i'll try to load and run them :)
I was hoping to find a way to image the entire server from the inside with some scripts to a remote server via ssh. A bit like VMware Converter did with the P2V function

Don't expect any "clone" of a running system to be without corruption.  But it might not be as bad as you think, since only those files with active changes are likely to matter. It isn't like a program or library will be changing, right?  The greatest risk is to a DBMS index and data files.  The solution for those is to use an export/dump-to-text facility that all DBMS systems have.

I don't use docker, but if you shutdown each docker instance, then their files will not be open and can be copied.  With LXD, the Canonical container manager, cloning a running container is built-in thanks to zfs which is the underlying file system used.

Imaging an entire system is a bad idea, BTW. It isn't like your new system has exactly the same hardware.  You should create a backup solution - i'd use a file-based, efficient, backup myself.  Images are huge for little payback.  With a good file-based backup, you should be able to selectively restore onto any other hardware.  Any system with 20GB of backup data should be restore-able in less than 45 minutes on completely different hardware.  I've used my restore process to migrate to a new release of the OS too at the same time switching hardware.  Alas, this isn't something anyone with less than intermediate skills should expect to be easy.

So, my suggestion is to work backwards from what is needed on the new system, and ensure your file-based backups include those things.  It took me 5 attempts to get everything necessary.  I've posted those things in these forums multiple times over the years.  If those posts aren't clear, then you'll probably want to find a different solution, but cloning really isn't viable. Sorry.

Using dd to clone a running system **will** result in corrupted files. The solution there is usually to boot off alternate media, so the OS isn't active at all, then clone. It will take lots of time to do a clone over the internet.  Whereas file-based backups that retain owner, group, permissions, ACLs and xattrs will be much faster and more efficient.  Be certain when doing the backups (whatever they are), that you use ssh-based tools to secure the channel between the source and target.

If you don't retain the owner, group, permissions, ACLs, and xattrs for each file object, then you don't really have a backup and you won't be able to get the software running on the new system.

---

