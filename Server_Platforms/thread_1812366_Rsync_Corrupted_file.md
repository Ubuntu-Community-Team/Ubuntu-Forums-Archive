---
title: "Rsync Corrupted file"
date: 2011-07-26
forum: Server Platforms
---

### Post by Jay89 on 2011-07-26
Hello,
   I have a linux box setup that's running ubuntu 8.04 I believe. And I have it setup so it will perform it's own backups every night using Rsync. I just noticed that it's been corrupting .PNG files, meaning that the image still opens but half of the image is cut off. The backups do not go over the network. The command I use is: 

rsync -avS --delete /storage/b/cur/ $BACKUPQUARTERLY/$TODAY/b >> $LOGFILE

Any and all suggestions will be greatly appreciated.

Thank You!

---

### Post by dtfinch on 2011-07-26
I use rsync heavily, and never had corruption. But I've never used the sparse option (-S), and a quick google search for "rsync sparse corruption" returns lots of results, so I'd suggest taking the S out.

Edit: Which filesystem is the destination?

---

### Post by Jay89 on 2011-07-26
> **dtfinch said:**
> I use rsync heavily, and never had corruption. But I've never used the sparse option (-S), and a quick google search for "rsync sparse corruption" returns lots of results, so I'd suggest taking the S out.

Edit: Which filesystem is the destination?
The same server but it goes from filesystem b to filesystem e. Both are _linux_ filesystems according to fdisk.

---

### Post by Jay89 on 2011-07-26
> **Jay89 said:**
> The same server but it goes from filesystem b to filesystem e. Both are _linux_ filesystems according to fdisk.
I just checked one of the affected files and it doesn't seem to be a  sparse file. So I did remove the -S option but still no luck...

---

### Post by Gyokuro on 2011-07-28
Maybe you should generate at first checksums of your files, rsync your files and compare later the checksums of both systems. Another idea is to compile your own static rsync binary and try your backup with the compiled one. You will also find information that --sparse and --inplace can generate corrupted files.

---

