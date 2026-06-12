---
title: "Is LUKS included in x64 8.04 Live CD?"
date: 2008-04-24
forum: Security
---

### Post by sunbird on 2008-04-24
I am running 7.10 with LUKS for full drive encryption and would like to do a clean install to 8.04. But, if the 8.04 Live CD doesn't have LUKS, I won't be able to mount my HDD for the install.

Anyone know?

---

### Post by bobotoes on 2008-04-24
depending on your options, you should be able to "apt-get install cryptsetup" and probe some modules (e.g. aes, dm-crypt) and mount the partition(s) on your own. I'm not sure how the ubuntu installer works though. In fact, I am wondering if the standard desktop install iso will allow me to setup a luks partition with lvm2. anyone?

---

### Post by sunbird on 2008-04-24
I can tell you that the 7.10 desktop will NOT allow you to encrypt. Only the alternate installer. But I don't know about 8.04.

I was thinking I could install cryptsetup. I am dling the 8.04 live cd now, so once I get it burned, I'll see if i can get LUKS up and running. I really hope that the Live CDs will include LUKS support and install-time encryption soon (if 8.04 doesn't already).

---

### Post by hyper_ch on 2008-04-25
I read some rumors that it was planend to incorporate onto the LiveCD as well.. but I think it wasn't included...

I also have to say it's been a long time since I used a live-cd the last time.

---

