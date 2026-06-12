---
title: "500gb usb hdd filesystem"
date: 2007-04-18
forum: The Cafe
---

### Post by thomas.hoyland on 2007-04-18
ok guys

i got a 500GB iomega usb2 external hdd on the way and im considering filesystems

maybe a 200/300 divide

but what filesystems do you recommend

its only going to be used on ubuntu so how about XFS?

any ideas are good

regards,
Tom

---

### Post by igknighted on 2007-04-18
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

Might be useful.  I have heard there are some drawbacks (like a crash can damage XFS more easily than ext3 or some others), but on a drive that large XFS sounds like it would suit you very well.

---

### Post by anaconda on 2007-04-18
I would use ext3.. it is good and well supported (even in windows) and old enough, so that there are some tools that can help you if it ever gets corrupted..

just remember to adjust the reserved blocks for root.. the normal 5% would waste 25GB of your disk. for root user only..

tune2fs -m 0 /dev/xxxx
will change the reserved blocks to 0%..

---

### Post by bullgr on 2007-04-18
if you use it to storage files, better use reiserfs, it's like ntfs in winblows.
you safe space because reiserfs uses smaller clusters and so it's good for small files too.

---

