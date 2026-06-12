---
title: "Ubuntu Server Dead After Power Outage. Currupt Kernal/launch"
date: 2010-12-12
forum: Server Platforms
---

### Post by Flash619 on 2010-12-12
Today we received about 12 inches of snow with power outages. After all of it my server would not start. Grub tries loading ubuntu server, and gives a error.

> 
error: Cannot read file.

error: "You need to load the kernel first"

I am able to boot up a rescue disk, but am lost as to what to do in order to fix it.  :oops:

For info I am using a x64 processor, with ubuntu server version 10.10

Is there some way to fix this without reformatting the entire thing. Possibly just re download the kernel? I would but I'm not sure how.

---

### Post by HermanAB on 2010-12-12
Howdy,

The problem is that the file system is likely corrupted, so you need to re-install and format.  So save your data using a live CD and get going...

---

### Post by Flash619 on 2010-12-12
Is there a way to back it up next time, so I don't have to completely start over?

---

