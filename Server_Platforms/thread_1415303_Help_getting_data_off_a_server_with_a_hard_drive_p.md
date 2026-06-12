---
title: "Help getting data off a server with a hard drive problem"
date: 2010-02-24
forum: Server Platforms
---

### Post by brian.m on 2010-02-24
I have a server running 8.04.2 that is on the fritz; the hard drive is failing (or at best somewhat corrupted) and I cannot boot unless in recovery move, where fsck fails and places the hard drive in read-only mode. Here are some details:


[LIST]
[*]Running fsck manually does not resolve the problem; I have done it a number of times but the drive is still mounted in read-only mode.
[*]I was able to start the SSH server to download files relating to the web services, but I need the MySQL database files as well.
[*]I cannot download anything from the /var/lib/MySQL directory because the files are owned by root.
[*]I cannot enable to root account because the hard drive is in read-only mode, and I cannot start the web services (phpmyadmin) for the same reason.
[*]I also cannot remotely SSH or SCP the files from the server to another because SSH is not part of the recovery mode environment.
[*]I cannot place the hard drive in another computer because it is encrypted (LUKS). I realize that it is possible to decrypt the drive but the tutorial I wrote that explains how to do this is in the MySQL database (it took me quite some time to put it together)!
[/LIST]

Can someone, please, provide some promising suggestions? I am running out of options to retrieve the last set of data (very important database files) off my server.

---

### Post by KiLaHuRtZ on 2010-02-25
Perhaps the superblock fsck is running against is corrupt or damaged.  When you create a filesystem (ext) is places backup superblocks on the disk based on filesystem size.  The first backup superblock is always 32.  Try fscking with that.

```
fsck -b 32 /dev/[DISK]
```

---

### Post by terazen on 2010-02-25
I don't know if something like this would help.  [http://www.newegg.com/product/product.aspx?item=N82E16812119152](http://www.newegg.com/product/product.aspx?item=N82E16812119152)

Or maybe put the hd into another server as a slave and see if it'll let you get in to copy data off it?

---

### Post by i.r.id10t on 2010-02-25
Boot with a live cd, then mount the drive and then chroot into the directory you have it mounted in - wallah! you are root.

---

