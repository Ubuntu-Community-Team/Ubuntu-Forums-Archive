---
title: "custom kernel stalls mounting encrypted hd"
date: 2008-06-15
forum: Security
---

### Post by dguido on 2008-06-15
Are there any specific options I should watch out for in my kernel config to support LUKS disks? I've compiled a custom kernel that gets as far as mounting my encrypted root device (mount by uuid=whatever) which then proceeds to tell me that the device can't be found. This might be related to the ATA controller drivers. Any thoughts would be appreciated.

---

### Post by hyper_ch on 2008-06-15
Well, do you have the according modules loaded?

aes_generic
dm_mod
dm-crypt

---

### Post by dguido on 2008-06-15
heh I got to that problem a few builds ago. The specific error I'm getting now is:

ide_media[1142]: main: unable to read from /proc/ide/ide0/hda/media

I'm going to play around with my ATA drivers a bit more. I must be doing something different from how the Ubuntu kernel is.

---

