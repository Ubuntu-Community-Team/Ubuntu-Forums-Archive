---
title: "Wipe"
date: 2010-08-07
forum: Security
---

### Post by diablo69er on 2010-08-07
Ok..so I read the man page on wipe, as well as various Internet articles stating that one pass is sufficient when it comes to wiping data.  I was using wipe with the following input:  wipe -i -f -c -P * in the directory that I wanted to remove the contents.  Now that should set it to one pass if i'm not mistaken, but in the terminal it usually goes up to 36 passes.

So what i'm really asking is 1 pass of wipe 36 passes over data?

Would I be ok to just remove the data with shred or something, my entire hd is Full Disk Encryption.

---

### Post by rookcifer on 2010-08-07
I've never used wipe since shred is pre-installed on most Linux distros.  To use shred do:

```
sudo shred -vf -n 1 /dev/sdx
```

Where sdx is the partition you want to overwrite.

The above will overwrite the partition with one random pass of data.  You can also overwrite individual files if you wish.

---

### Post by bodhi.zazen on 2010-08-08
> **diablo69er said:**
> Ok..so I read the man page on wipe, as well as various Internet articles stating that one pass is sufficient when it comes to wiping data.  I was using wipe with the following input:  wipe -i -f -c -P * in the directory that I wanted to remove the contents.  Now that should set it to one pass if i'm not mistaken, but in the terminal it usually goes up to 36 passes.

So what i'm really asking is 1 pass of wipe 36 passes over data?

Would I be ok to just remove the data with shred or something, my entire hd is Full Disk Encryption.

You are almost certainly good to go with full encryption.

If you want to know, one pass is sufficient, you can use dd to fill your free space with 0's or ones daily with a cron script.

The Gutmann theory has been debunked:

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html")

---

