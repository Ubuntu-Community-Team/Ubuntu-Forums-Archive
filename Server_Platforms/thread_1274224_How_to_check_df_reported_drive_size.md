---
title: "How to check df reported drive size"
date: 2009-09-24
forum: Server Platforms
---

### Post by rocknrollmouse on 2009-09-24
I have ubuntu 6.10 server with two 400G drives configured in mdadm RAID1 (software mirror).  


If I check the free space with df -h I'm told there's 33G used out of 48G; 
however running fdisk -l or mdadm --detail for the same drive, 
I'm told its 398G (no used space info).

The used space at just over 30G's sounds about right, but the drive size is drastically worrying (expecting the fdisk or mdadm result).
Does anyone know of a problem with df or is there another way to check drive size?

---

### Post by 3L33T on 2009-09-24
[Why DF and DU report a different sizes]("http://bit.ly/exzCH")

---

### Post by scorp123 on 2009-09-24
> **3L33T said:**
> [Why DF and DU report a different sizes]("http://bit.ly/exzCH")

That ... and the fact that 5% of a drive are being reserved for "root" (true for Ext3 and Ext4; other filesystems possibly too). If you have a really large drive those 5% soon add up.

So what I do is I decrease that size down to 1% or even 0.5% via the "tune2fs" utility.

---

### Post by rocknrollmouse on 2009-09-28
> **scorp123 said:**
> That ... and the fact that 5% of a drive are being reserved for "root" (true for Ext3 and Ext4; other filesystems possibly too). If you have a really large drive those 5% soon add up.


So 5% of the drive could be being reserved for root, 5% of 398 = 20G
Current data on drive is 30G
If I'm understanding what you're saying scorp123, the 398G drive might only show as 378G (ie 398 - 20)
thats still quite a long way out from the 48G df is reporting.

3T33L, if I'm understanding your link; discrepancies between df and ds can exist because: other users can be on the system, and/or files may have been deleted.
Unfortunately, I don't think either of these apply here, as:
[LIST]
[*]size checks ran at console out-of-hours (ie whilst users were off-line);
[*]physical drives have recently been upgraded from 36G drives, and users have not had access to create & delete files at time of check;
[*]discrepancy is between df and fdisk -l 
or between df and mdadm --detail
[/LIST]

Whilst I could (and probably will) try running:
```
tune2fs -m 0 /dev/md0
tune2fs -r 20000 /dev/md0
```
(as recommended in this [how to post]("http://www.neowin.net/forum/index.php?showtopic=623460"))
but this seems a little unlikely to return an additional 350G of drive space?

---

### Post by rocknrollmouse on 2009-10-05
bounce

---

