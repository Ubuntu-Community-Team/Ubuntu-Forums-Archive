---
title: "Encrypted lvm / dd backup question"
date: 2009-09-15
forum: Security
---

### Post by Fluffy13 on 2009-09-15
I am using Intrepid 8.10 and i installed it with the alternate cd as an encrypted lvm. My question is:

If i create a backup using the following method, can i then format, setup an encrypted install on my new hard drive, and then restore the image without issue?

```

dd if=/dev/sda1 of=/home/steve/sda_partition.image bs=4096 conv=notrunc,noerror
```and restore it using:

```

dd if=/home/steve/sda_partition.image of=/dev/sda1 bs=4096 conv=notrunc,noerror
```

---

### Post by shaggy999 on 2009-09-16
I'm not sure if that will work in terms of the partition being recognized after a clean install, but one point I would make is that your image will not be compressible because, by nature, encrypted data should appear random and compression algorithms work on finding patterns in data.

If you are running the backup from the running system you could perhaps run dd on the lvm like /dev/mapper/system-root and then the output of dd could be run through bz2 or gzip or whatever and then the output of THAT could be encrypted with gpg or something. If you zero out your empty sectors beforehand this will result in a MUCH smaller dd image. This, of course, may not be an issue for you if you have tons of space.

Then to re-image the drive you could open the lvm encrypted partition and write the dd image back to that.

That's my .02.

---

### Post by Fluffy13 on 2009-09-16
i have a terrabyte external so im not real concerned with the image size. I just want to find out if the method will even work

---

### Post by shaggy999 on 2009-09-16
You can always test it. Perhaps image the entire hard drive in its current state for fail-safe backup and then try your method and see if it works. If not, just re-image the backup.

---

### Post by lensman3 on 2009-09-17
I would suggest some other program that doesn't copy the files from root (the slash).  If you ever want to restore, then you can only restore from root.  Both "tar" and "star" will backup and strip the first slash.  Look for backup programs that have the -xdev flag.  -xdev will backup only those files that are on the start partition.

I don't know if you do a restore on dd where you have backed up an entire partition from root, if it can restore under a sub directory.

---

