---
title: "Issues with Keyboard while Installing 9.10 Server Edition"
date: 2010-04-02
forum: Server Platforms
---

### Post by RagnarIV on 2010-04-02
Hello,

I've been using server 9.10 for my home servers for a while now. I am still a nOOb however. I built a server to host a blog and to run remote backups from a remote location. Now, its been cobbled together from parts I had lying around. The specifications are:

AMD X2 3800+
Jetway Socket AM2 Geforce 6100 Motherboard
4 GB DDR2 800
Liteon ihas 2014 DVD Burner
Maxtor 60Gb IDE drive
550w Coolermaster PSU
Apevia GamerX server case

Regardless, the system posts fine, recognizes any keyboard I plug in, but when it boots into the Ubuntu installation CD The language selection pops up and I cannot select anything. I've tried two different keyboards and nothing seems to work. Only commonality between the two is that they are both USB based. Any ideas?

---

### Post by BobVila on 2010-04-02
> **RagnarIV said:**
> Hello,

I've been using server 9.10 for my home servers for a while now. I am still a nOOb however. I built a server to host a blog and to run remote backups from a remote location. Now, its been cobbled together from parts I had lying around. The specifications are:

AMD X2 3800+
Jetway Socket AM2 Geforce 6100 Motherboard
4 GB DDR2 800
Liteon ihas 2014 DVD Burner
Maxtor 60Gb IDE drive
550w Coolermaster PSU
Apevia GamerX server case

Regardless, the system posts fine, recognizes any keyboard I plug in, but when it boots into the Ubuntu installation CD The language selection pops up and I cannot select anything. I've tried two different keyboards and nothing seems to work. Only commonality between the two is that they are both USB based. Any ideas?

I've had odd problems with USB keyboards in the past. If you've got a ps2 keyboard around, i'm sure it'll work. Otherwise, check your BIOS USB settings.

---

### Post by KB1JWQ on 2010-04-03
Yeah, check Legacy USB support in the BIOS-- toggle that perhaps?

---

### Post by RagnarIV on 2010-04-07
Yeah, I had already checked the USB keyboard options in the BIOS. I also got a USB to PS/2 adapter, and it made no difference. I'll fiddle with it some more.

---

