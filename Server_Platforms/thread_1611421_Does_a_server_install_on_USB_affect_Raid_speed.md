---
title: "Does a server install on USB affect Raid speed?"
date: 2010-11-01
forum: Server Platforms
---

### Post by kenada on 2010-11-01
Hi,

I have a home file server which is running out of space, so I was looking to add a drive to my existing raid 5 array. 

Unfortunately I'm out of SATA spots as well, so rather than looking to get a potentially expensive raid controller, I thought I could install Ubuntu on a USB stick and use the SATA port for another drive in the raid.

So I was just wondering if there was any trade off on doing this? speed wise or i/o access due to the USB install?

Anyone have a similar setup?

Thoughts?

---

### Post by arrrghhh on 2010-11-01
If you have a hardware RAID controller then what you describe will not work.  You'd have to build the RAID in mdadm, software-RAID.  Yes, I would think speed would be diminished, basically the point of hardware-RAID is the array is OS indepedent and fast!

With all that said, I imagine it would be doable with a performance hit.  Make sure the external drive is the same size as all of the other drives as well!

---

### Post by kenada on 2010-11-01
Sorry, I should have specified. I did mean Software-Raid.

---

