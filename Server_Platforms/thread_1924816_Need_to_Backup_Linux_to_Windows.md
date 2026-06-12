---
title: "Need to Backup Linux to Windows"
date: 2012-02-13
forum: Server Platforms
---

### Post by JAZ1976 on 2012-02-13
Hi Everyone,

I'm looking for a way to backup my companies Ubuntu 11.10 Server to a windows backup location. This Ubuntu server is the only Linux box we have in my company. I was looking into rsync, but it seems like it may only be for Linux to Linux backups. Can rsync be used for Linux to Windows, or do I need to look for another solution?

Thanks,
JAZ

---

### Post by collisionystm on 2012-02-13
> **JAZ1976 said:**
> Hi Everyone,

I'm looking for a way to backup my companies Ubuntu 11.10 Server to a windows backup location. This Ubuntu server is the only Linux box we have in my company. I was looking into rsync, but it seems like it may only be for Linux to Linux backups. Can rsync be used for Linux to Windows, or do I need to look for another solution?

Thanks,
JAZ



mount your windows computer on the Ubuntu server and use rsync.
Essentially you make a folder for your windows box, mount the server there and you can just backup to it as if it was a folder on the server.

If this sounds like something you want I can help you do it

---

### Post by TheFu on 2012-02-13
If all you want is to backup the data, then you just need a way to copy the data.  **rsync** alone fails at being a good backup solution, though it is fantastic as a mirroring method.  For purely data backups, not operating system or DBMS backups, something like **rdiff-backup** would work.  You'll probably want to use a CIFS mount to the remote computer, but there are lots of ways to do what you want.

**tar** might be useful, but doesn't deal with incremental backups efficiently when stored on disk.

Many ways of backing up a Linux server to Windows will lose file ownership and permissions. That makes it nearly worthless if OS and application backups.  Since Linux is usually small, doing an image-based backup with something like partimage might be useful ... for the base OS.  It also works for Windows, BTW.

There are other backup tools, but most of them work the other way - Windows to Linux server.  **Bacula**, **Duplicati**, **Duplicity**, etc ... are all options.  There are others.

Of course if you already use a commercial tool under Windows, there is probably a Linux client available too. **Netbackup** has one for these Linuxen:

[LIST]
[*]Red Hat
[*]SUSE
[*]Novell OES Linux
[*]Asianux/RedFlag
[*]Debian/CentOS/Ubuntu
[/LIST]
**Best Practices for Backups** has more details: 
[http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups)

---

### Post by JAZ1976 on 2012-02-13
Both of you, thanks for the quick replies. I like the rsync to a Windows share mounted directly to linux, that collisionystm suggested. It would get me up and running quickly, and it may be all I need. The Linux server is running as a virtual serve hosted on a HyperV server. The HyperV image of the server is being backed up, so we can restore the whole server if something catastrophic happened. We are also doing a tape backup of the directory that I am looking to rsync. I was going to use the rsync so I could go directly to that on a restore and have the tape as an offsite. Does that sound like a good solution TheFu?

---

### Post by josephpmh on 2012-02-13
> **JAZ1976 said:**
> Hi Everyone,

I'm looking for a way to backup my companies Ubuntu 11.10 Server to a windows backup location. This Ubuntu server is the only Linux box we have in my company. I was looking into rsync, but it seems like it may only be for Linux to Linux backups. Can rsync be used for Linux to Windows, or do I need to look for another solution?

Thanks,
JAZ

rsync will work from your Ubuntu server to the windows backup location (wbl).  It would be simpliest to mount the wbl on your server

```
 mount -t cifs [//your server's ip address/sharefolder] /[server]/[mountpoint] -o username=[yourwindowsusername],password=[yourwindowspassword],rw 
```


followed by

```
rsync -avrP /[yourserver/ /[server]/[windowsmount] 
```

the options are a(rchive), v(erbose), r(ecursive) and P(artial).  

Once mounted, you can also use the dd command:

```
dd if=/[yourserver] of=/[server]/[windowsmount] bs=[desired block size (e.g. 4M)]
```

I like rsync's incrementality (altho there are ways to use dd to backup incrementally).  I also like rsync's ability to pick up where it left off should there be a power outage, or I turned off the machine to which it was syncing, or you just wanted to reboot your server.  With both, you can run it, then go and do something else while waiting for the operation to complete.

You might also want to take a look at Adrian Klaver's article for Linux Journal on rdiff.  ([http://www.linuxjournal.com/article/10701](http://www.linuxjournal.com/article/10701))  It tells the pros and cons of rsync vs rdiff and gives pretty detailed instructions on its use.  If you've a lot of data, read this. 

Have fun.  That's why we're here.


</SOPA> </PIPA>

---

### Post by HermanAB on 2012-02-13
The best thing you can do with a Windows machine is to install Cygwin on it.

---

### Post by JAZ1976 on 2012-02-13
josephpmh,

Thanks for the reply. When rsyncing to a Windows share, do the files the keep their permissions that they had when you bring them back over. Also, do I have to do anything to the mount location to keep the mount point if the server is ever rebooted? Lastly, how does rsync deal with files that are open?

---

### Post by TheFu on 2012-02-14
> **JAZ1976 said:**
> Both of you, thanks for the quick replies. I like the rsync to a Windows share mounted directly to linux, that collisionystm suggested. It would get me up and running quickly, and it may be all I need. The Linux server is running as a virtual serve hosted on a HyperV server. The HyperV image of the server is being backed up, so we can restore the whole server if something catastrophic happened. We are also doing a tape backup of the directory that I am looking to rsync. I was going to use the rsync so I could go directly to that on a restore and have the tape as an offsite. Does that sound like a good solution TheFu?


**Rsync is not suitable for most backup requirements**. Sorry.  If you can figure out rsync, then you can figure out rdiff-backup.  The commands are almost the same and it provides soooooo much more capability from a backup and recovery perspective.

Rsync is fine for huge media files that never change, but not for .DOC or emails or other files that change all the time.

Backups need to support restores of the files from yesterday, last week and 22.6 days ago. rdiff-backup does.

---

### Post by JAZ1976 on 2012-02-14
Thanks TheFu,

You have been very helpful. I will look into rdiff-backup today. 

JAZ

---

### Post by perspectoff on 2012-02-14
cp -a

works and keeps permissions (but doesn't do differential backups).

I copy my entire server periodically (onto an old Windows backup drive) using this mainly because it keeps permissions intact.

Much easier than partimage or Clonezilla or anything like that.

Here's how I use it:

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric_System_Backup#cp](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_System_Backup#cp)

---

### Post by SeijiSensei on 2012-02-14
Doesn't that example use ext4 filesystems as the target destinations, not a Windows filesystem like NTFS or FAT32?

Frankly the only good solution I can think of for backing up to a Windows filesystem is to create a compressed tarball of the entire Linux system and copy it to the Windows backup.  That approach has the obvious disadvantage that it cannot be updated with individual files, but it will create an image of the entire filesystem with permissions intact.

---

