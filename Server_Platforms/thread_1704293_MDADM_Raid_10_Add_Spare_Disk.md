---
title: "MDADM Raid 10 Add Spare Disk"
date: 2011-03-10
forum: Server Platforms
---

### Post by NedHanlon on 2011-03-10
This is probably covered somewhere else, but I could not find it. If it is, a link to that forum will suffice. 

I have a raid 10 array that I created when I installed Ubuntu Server 10.10. When I installed it, it gave me the option of installing a spare drive, which I did not take. I now have a spare drive I would like to use. Is it possible to install it now? If so, how would I do that. If not, do I need to reinstall the OS? 

Also, once I have a spare drive, will it automatically take the place of a failed drive? Or will it need human intervention. 

Let me know if you need any more data. 

Thanks.
--
Ned Hanlon

---

### Post by rubylaser on 2011-03-10
Adding a spare is very easy, just open up a terminal.  Then partition, your disk, and add it to the array as a spare.  This is an example where /dev/md0 is your array, and you're added /dev/sdh1 as a spare.
```
mdadm &#8211;add /dev/md0 /dev/sdh1
```

If you look at the output of 
```
cat /proc/mdstat
```
you'll see the device listed as a spare.

And if a drive fails, yes, it will automatically use the spare as a replacement device.

---

### Post by NedHanlon on 2011-03-10
Thanks! Worked Perfectly.

---

### Post by rubylaser on 2011-03-10
No problem, glad to hear that you got it working so quickly.

---

