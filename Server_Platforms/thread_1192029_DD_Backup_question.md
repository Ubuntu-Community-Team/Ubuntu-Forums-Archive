---
title: "DD Backup question"
date: 2009-06-19
forum: Server Platforms
---

### Post by terazen on 2009-06-19
When using dd I found that it creates an image of all the free disk space.  Is there a way with dd or another program to create an image of a live ubuntu server without the free disk space?

---

### Post by HermanAB on 2009-06-19
Clonezilla

---

### Post by cariboo on 2009-06-19
Partimage functions the same as dd, except it doesn't clone the empty space. Partimage is in the repositories.

---

### Post by sgosnell on 2009-06-19
Remastersys should also work.

---

### Post by terazen on 2009-06-19
Could any of these create images of the server while it is live?

I was under the impression that partimage and clonezilla would require reboots?

I'll look them up again.  Haven't read about Remastersys yet.  Will do it now.

---

### Post by windependence on 2009-06-19
If you compress the image, the freespace should be small and negligible because it contains all zeros:

```
dd if=/dev/sda1 ibs=4096 | gzip > partition.image.gz conv=noerror
```To restore the compressed image:

```
dd if=partition.image.gz | gunzip | dd of=/dev/sda1
```-Tim

---

### Post by terazen on 2009-06-19
Freespace isn't necessarily 0's.  The machine I tested dd on had a ~70GB harddrive and only 2GB used.  The dd image filled up the entire harddrive to 100%.

---

### Post by Brandon Williams on 2009-06-19
It's true that the free space won't typically be 0's, but it's easy enough to write 0's to it. When I use dd to take a snapshot image, if first use 'dd if=/dev/zero of=delete.me' to write a file of 0's that fills up all the free space on the parition. After that, the compressed image takes up significantly less space that it otherwise would have. For example, a compressed image of my half-used 8GB SSD takes less than 1GB of storage space. Without the /dev/zero trick, the compressed image will often take up twice as much space.

---

### Post by windependence on 2009-06-19
Either way, the free space will compress nicely. If you write all zeros, even better. Thanks Brandon, for the clarification.

-Tim

---

### Post by sgosnell on 2009-06-19
Remastersys doesn't require a reboot.  It backs up your system entirely, or partially, whatever you choose.  It's in the Ubuntu repositories.

---

### Post by terazen on 2009-06-20
Thank you, the trick to use dd with /dev/zero worked like yall said.  I did something to the effect of this:
```
sudo dd if=/dev/zero of=/tmp/delete.me
sudo rm /tmp/delete.me
sudo dd if=/dev/sda1 ibs=4096 bs=2048 | gzip > /tmp/nms-server-dd-img.gz

```

I do have one question though.  When the dd if=/dev/zero command finishes and fills up the harddrive, will that impact websites using mysql and such?

I'll try remastersys early next week.  Thanks for all the help.

---

### Post by windependence on 2009-06-20
It's only writing zeros to the freespace on the drive. There may just be random data on there now, or it may contain just zeros if it hasn't been written to before. It doesn't affect any of the live data on the drive. Since the free space is all the same data it essentially takes up almost no space. The compression algorithm just marks it as all the same from x block to y block without storing all the zeros. Compression algorithms don't store the data, they just describe the data, so the more the datat is the same, the better it compresses.

-Tim

---

### Post by Brandon Williams on 2009-06-21
Anything you do that completely fills up the disk while there is other activity on the system could have a negative impact on any other process that needs to write new data to the disk. A mysql database may need to do this when adding records. A web server may need to do this when writing logfile records. The files used by those processes will most likely have enough extra spaces in their blocks to get you past this if you delete the file immediately, but any process that needs to create a completely new file will have trouble.

You can minimize the risk leaving a handful of disk blocks untouched. Simply use df to figure out how much space is currently available on the disk and then subtract a reasonable amount to account for disk usage during the operation. For example, my SSD currently has 3180848 bytes available, which is roughly 776 4K blocks. This command line: 'sudo dd if=/dev/zero of=/tmp/delete.me bs=4096 count=750' will tell dd to create a file with 750 4K blocks worth of zeros, leaving 26 blocks for short-term use by other processes. That way, you still get the compression benefit of having zeroes on most of the free space without too much risk of other processes being negatively impacted.

---

### Post by terazen on 2009-06-21
You all are so awesome.  Thanks!

I really need to find a good book for all this and sit down on it.  Just gotta catch up on some other certs and maybe I'll have time in between semesters one of these days...

---

### Post by windependence on 2009-06-22
> **Brandon Williams said:**
> Anything you do that completely fills up the disk while there is other activity on the system could have a negative impact on any other process that needs to write new data to the disk. A mysql database may need to do this when adding records. A web server may need to do this when writing logfile records. The files used by those processes will most likely have enough extra spaces in their blocks to get you past this if you delete the file immediately, but any process that needs to create a completely new file will have trouble.

You can minimize the risk leaving a handful of disk blocks untouched. Simply use df to figure out how much space is currently available on the disk and then subtract a reasonable amount to account for disk usage during the operation. For example, my SSD currently has 3180848 bytes available, which is roughly 776 4K blocks. This command line: 'sudo dd if=/dev/zero of=/tmp/delete.me bs=4096 count=750' will tell dd to create a file with 750 4K blocks worth of zeros, leaving 26 blocks for short-term use by other processes. That way, you still get the compression benefit of having zeroes on most of the free space without too much risk of other processes being negatively impacted.

Just a note, this is not necessarily true since you are writing zeros, but you are leaving it as free space, IOW you are NOT putting an entry into the file allocation table telling it there is data there, so the actual applications see it as free space only. I would certainly suggest stopping your other services while doing this, but after it is finished there should be no impact other than nice tight data on the disk which will actually help performance not hurt it.

-Tim

---

### Post by m0nk3ym@n on 2009-06-22
Partimage is good, and it will give you everything you need for a bare metal restore:

[http://urlbop.com/3/9z5sf4](http://urlbop.com/3/9z5sf4)

---

