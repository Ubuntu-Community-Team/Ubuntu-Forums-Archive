---
title: "rsync between Windows share and ubuntu in different states"
date: 2010-08-04
forum: Server Platforms
---

### Post by blind0wl on 2010-08-04
Hi there,  I am trying to figure out a way of mirroring a drive in one city to another city.  There is currently 300gig of files and we have had a external USB drive with a copy of all the data sent up to our office.

I have attached this drive to one of our Ubuntu boxes and setup a samba share to the Windows share in the other state.  I then have been running rsync on the local Ubuntu box to the Windows share.  The link to the other state is not that impressive but it should do the job...all I'm after is for the drive to mirror any changes on the primary city drive.

I'm finding when I run:
```
rsync -avz --progress /mnt/windowsshare/ mnt/usdbisk
```

the reference list takes so long to finish...so far it's been going for 3 hours and I'm only running the --dry-run option atm.  Is there a better way of doing this?  Will it be faster next time?  The drives atm are exactly the same and I'm not expecting any file transfer to take place.

Cheers

Blindy

---

### Post by blind0wl on 2010-08-04
This was the output from the rsync...ended up taking 12 hours.

```
sent 9545087 bytes  received 1468168 bytes  386.74 bytes/sec
total size is 354069944984  speedup is 32149.44 (DRY RUN)
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1060) [sender=3.0.7]

```

---

### Post by cj.surrusco on 2010-08-04
386 b/s is *extremely* slow. What type of network connections are you using on each end?

---

### Post by blind0wl on 2010-08-04
The SNMP graphs I've been looking at have been seeing 6MB/s running through the pipes at one stage or another...it's currently a managed mesh service and is supposed to pick the fastest links back down to the other state.

I may try it tonight again and see if there is any difference as it will be quieter in the evening.

General traffic yesterday was not high though.

Thanks for the reply

Blindy

---

### Post by dtfinch on 2010-08-04
You can use the --times option to make rsync assume that files with the same size and modify date are unchanged. If the source and destination filesystems are different (seems likely), you'll want to use --modify-window=60 (or any other sufficient number of seconds) to prevent it from mistaking time rounding differences for real differences.

I haven't actually used rsync to copy from a windows share, since it sort of defeats all of rsync's network optimizations. For backing up files on Windows servers I use a Windows port called cwRsync, and connect to that. It should be faster that way, especially if you need to backup large files that change only slightly each day. Rsync connecting to itself only transfers what has actually changed.

Something that's probably not your bottleneck here but it would be if you were copying over a lan is if the usb drive is formatted ntfs. I've had pretty big slowdowns rsyncing to an ntfs formatted usb drive, with the ntfs driver consuming ~99% of the cpu. Nightly updates (millions of files) went from 5 hours to about 30 minutes going to ext3.

Something else to watch for down the road backing up Windows shares is locked files. It's common for Windows apps to lock files deny_read, making traditional copying impossible. You need volume shadow copies to get at those reliably. If it's just a few known files, it might be enough to schedule another tool like hobocopy to make unlocked copies that can be backed up by rsync.

---

### Post by blind0wl on 2010-08-05
Ran it last night and here are the results with the added options you mentioned:

```
Number of files: 476262
Number of files transferred: 436725
Total file size: 354070103227 bytes
Total transferred file size: 354070103227 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 8077588
File list generation time: 21.654 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 9545930
Total bytes received: 1468325

sent 9545930 bytes  received 1468325 bytes  423.11 bytes/sec
total size is 354070103227  speedup is 32146.53 (DRY RUN)
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1060) [sender=3.0.7]

```

Problem I have is that the other drive is on a Windows server that the IT guys dont want to muck about with, so adding programs to it isn't an option.  It is on an NTFS partition, but again it's not something I can change due to it being connected to a Windows machine.

I'm hoping there wont be any issues with file locking as it's basically just a repository of data and not something people would open things on, but rather download them and use them on their own PC's.

Thanks for the great response to my issue...not sure where to go now though...I may just be stuck with this terrible speed.  The only other thing I thought of was possibly lftp to mirror the drive as there is a ftp server running pointing to the archive...but I have read that it's quite inefficient in comparison to rsync.

Cheers

Blindy

---

### Post by blind0wl on 2010-08-05
The one thing I don't quite get is this snippet:

```
Total file size: 354070103227 bytes
Total transferred file size: 354070103227 bytes
```

Is it actually transferring that data?  It shouldn't be as the drive I have locally is all ready a mirror of the data...I could just be reading that wrong though....

---

### Post by dtfinch on 2010-08-06
In the case of rsync connecting to itself the sent/received bytes would be the important values. But running in local mode, where it has no way of really knowing what data has changed without reading it entirely over the network, I wouldn't be surprised if it was reading every file, if the file properties looked different somehow to warrant a comparison.

The -a option you used implies -rlptgoD. The l, p, g, o, and D options (preserve links, permissions, groups/owners, and devices) probably don't translate well to a Windows server, and might be causing it to think every file has potentially changed. So you could try replacing the -a with -rt. And the -z (compress) option is meaningless in local mode, so you can leave it off.

---

