---
title: "Access GRUB and break into full encryption drive?"
date: 2015-05-17
forum: Security
---

### Post by Rytron on 2015-05-17
Hi.

I have full disk encryption on Ubuntu-MATE 15.04. I notice that I can get to GRUB before being asked for the disk decryption password. Can someone access GRUB and break into my encrypted hard drive? I'd think not but would just like some input on this.

Thanks.

---

### Post by TheFu on 2015-05-18
They can attack your encrypted drive. Does that mean that anyone can break it? I dunno. Some reading:
* [https://www.schneier.com/blog/archives/2012/12/breaking_hard-d.html](https://www.schneier.com/blog/archives/2012/12/breaking_hard-d.html)
* [http://www.jakoblell.com/blog/2013/12/22/practical-malleability-attack-against-cbc-encrypted-luks-partitions/](http://www.jakoblell.com/blog/2013/12/22/practical-malleability-attack-against-cbc-encrypted-luks-partitions/)
* [http://www.irongeek.com/i.php?page=videos/bsideslasvegas2013/5-1-1-attacking-and-defending-full-disk-encryption-tom-kopchak](http://www.irongeek.com/i.php?page=videos/bsideslasvegas2013/5-1-1-attacking-and-defending-full-disk-encryption-tom-kopchak)

There is an attack technique where the boot code on your device is replaced with modified code and wait for you to enter the credentials to unlock the storage, storing those or transmitting them elsewhere. Attackers can be patient at this level.  If you are paranoid enough, you might want to only boot off a portable device that you keep with you always - at least when travelling. That includes going into the shower, toilet, etc ... when staying in hotels so the **evil maid attack** is useless.

For anyone who travels overseas, it might be useful to have a small bootable Linux install that can be used to show a working device or let border control at different locations around the world see a fresh install  with ZERO data.  A minimal install should fix in 4G and suffice to prove a working system.  Other partitions would be encrypted and unused in this "demo" mode boot. i'd make the demo-mode the default boot too.

Of course, rubber hose unlocking techniques will still exist.

---

### Post by Rytron on 2015-05-19
Thanks for the links. The video was particularly informative. ):P

---

### Post by HermanAB on 2015-05-20
The boot partition is not encrypted.  The machine has to start up somehow.

---

### Post by Rytron on 2015-05-20
> **HermanAB said:**
> The boot partition is not encrypted.  The machine has to start up somehow.

True. ;)

---

