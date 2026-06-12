---
title: "Full disk encryption, suspend, and hibernate"
date: 2009-08-25
forum: Security
---

### Post by shaneh on 2009-08-25
I didn't know where else to put this. I thought that some of you (and any future googlers) might be interested to know that over the weekend I went with the default LUKS install of 9.04 on a new computer, and **hibernate/suspend work just fine**. It seemed like people were unsure of whether that was true or not when I read [this thread]("http://ubuntuforums.org/showthread.php?t=1176764").

Context (the only configuration I know works for sure):
Ubuntu 9.04, 64-bit alternate install CD with all default settings for LUKS full disk encryption
No other Operating Systems or distros
Dell Studio XPS 13 (aka 1340)
256 GB Dell-branded SSD
NVIDIA GeForce 9400M
Restricted drivers for NVIDIA and Broadcom

Everything went smoothly and worked perfectly pretty much from the get-go. I'm assuming it wouldn't be too difficult to get this to work properly with a more customized partition scheme, dual booting, etc. I'm also seeing no perceptible loss in performance. 

When you wake from hibernation, you have to give passphrase to decrypt, just like booting normally.

From what I understand, though - suspend still stores the crypto key somewhere in memory so your machine is still vulnerable in this state. Still, it's really convenient to have, and users should be able to weigh the costs/benefits and make their own decisions on whether (and if so, when) to use suspend or not.

Thanks to everyone who has given information, put together tutorials, etc. on full disk encryption on this forum. I read probably hundreds of posts from dozens of threads before I really felt confident doing this.

---

### Post by dalesd on 2009-10-27
thanks, shaneh.  I'm going to do this when Karmic is released.  

Whole disk encryption FTW!

---

