---
title: "server question on partitions"
date: 2007-01-12
forum: Server Platforms
---

### Post by brtp on 2007-01-12
Greetings all,    I have a question and hope a kind soul or 2 will shed some light,  I have built a server,  twin pIII  1gig rdram and 4 80gig hd's 3 primary and a slave,   ideas on the best way to partition the drives,  I have well over 100 gigs of mp3's and other staorage needs such as programs,  data, docs, pics and such,,, any and all suggestions would be appreciated  thnx in advance

---

### Post by Brazen on 2007-01-12
My suggestion would be to use one drive as as your system partition.  Put your /boot, /, and swap partitions on that one drive.

For the other three, partition the entire drives as raid partitions, and combine those 3 raid partitions into a Raid5 device.  Partition that device and mount it where you want to store all your files.  That way your important files will be protected in case of a harddrive failure.  Your system files and programs will not be protected, but those are easy to just re-install anyway.  The Raid3 array would give you 160GB of storage space.

The other option would be to just combine all four drives with LVM, which would give your roughly 320 GB of storage, but you would have no protection from a harddrive failure.

---

