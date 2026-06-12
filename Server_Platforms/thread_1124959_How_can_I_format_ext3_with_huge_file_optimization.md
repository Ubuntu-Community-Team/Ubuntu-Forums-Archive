---
title: "How can I format ext3 with huge file optimization?"
date: 2009-04-13
forum: Server Platforms
---

### Post by TomB19 on 2009-04-13
I have a 4.5 TB mdadm RAID5 array that is formated ext3.  It doesn't have anything on it yet.  I can re-RAID or re-format on a whim.

The install cd allows for huge file optimization for ext3 partitions.  How can I do that from the command line?

This drive is going to contain a few dozen huge backup tar balls.

---

### Post by HalPomeranz on 2009-04-13
```
sudo mkfs -t ext3 -T largefile4 /dev/sd<whatever>
```

Substitute the appropriate partition designator for your RAID array in place of <whatever> in the command above.

---

### Post by TomB19 on 2009-04-13
Thank you!  :)

---

### Post by Innom on 2009-04-14
You might want to think about stripe size and stride while you've got a blank slate :)

This is a very handy script :)

[http://busybox.net/~aldot/mkfs_stride.html](http://busybox.net/~aldot/mkfs_stride.html)

---

