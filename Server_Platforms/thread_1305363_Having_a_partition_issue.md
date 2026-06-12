---
title: "Having a partition issue"
date: 2009-10-29
forum: Server Platforms
---

### Post by ExTruckie on 2009-10-29
Hello

I have set up a file server on my network using the instructions posted at Knightwise.com [http://www.knightwise.com/content/view/300/9/](http://www.knightwise.com/content/view/300/9/)  I know these are dated because of the release of Ubuntu used, but it all worked!!

I have a small issue and need a solution. I am using Ubuntu desktop machine as a file server and eventually a print server. I have my hard drive partitioned as such 7.82Gb 
/dev/sda1 ext3 and 20.13Gb /dev/sda2 fat32. I can set up my windows shares to see the primary partition but I can not see the second partition. I want to keep the data and the OS on seperate partitions. 
My question is, how do I see the second partition?
on a related note,  how would I get any additional hard drives installed to be seen also?

Thanks to all you learned peeps.

---

### Post by Vegan on 2009-10-30
you need to mount them off /

I used the unimaginative name /disk2 and pointed my mount there. I then pointed SAMBA to use it.

make sure you update /etc/fstab

---

### Post by ExTruckie on 2009-10-30
> **Vegan said:**
> you need to mount them off /

I used the unimaginative name /disk2 and pointed my mount there. I then pointed SAMBA to use it.

make sure you update /etc/fstab


Thanks 
I got it setup the way I wanted

---

