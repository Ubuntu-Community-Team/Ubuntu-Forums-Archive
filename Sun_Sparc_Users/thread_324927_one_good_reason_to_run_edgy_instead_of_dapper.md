---
title: "one good reason to run edgy instead of dapper"
date: 2006-12-24
forum: Sun Sparc Users
---

### Post by yonderway on 2006-12-24
So I've been playing with various Linux and BSD distributions on my "new" Enterprise 250 (E250).  I do enjoy Ubuntu so I've tried both dapper and edgy on it.

So I have dapper running.  Everything looks good except disk I/O is lousy.  I do an "hdparm -Tt /dev/sda" to get some idea of what the disk performance is like.  Keep in mind, the controller is good for 40MB/sec but the drive is probably only good for about 30MB/sec so I expect a number in that ballpark.  Here is what I get:

```
/dev/sda: 
 Timing O_DIRECT cached reads:   888 MB in  2.00 seconds = 443.09 MB/sec
 Timing O_DIRECT disk reads:   22 MB in  3.24 seconds =   6.80 MB/sec
```

Eww.

I look in the dmesg and find an interesting bit:
```
target0:0:0: FAST-20 SCSI 20.0 MB/s ST (50 ns, offset 16)
```

Ummmm not good.

Now with edgy running it's a different story.
```
target0:0:0: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 16)
```

That's promising!

```
Timing O_DIRECT disk reads:   90 MB in  3.05 seconds =  29.51 MB/sec
```

Bingo!  Just what I had been hoping to see all along.

---

