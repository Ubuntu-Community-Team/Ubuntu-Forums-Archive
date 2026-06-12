---
title: "How to mount ISO in Wine"
date: 2009-11-02
forum: Wine
---

### Post by chkneater on 2009-11-02
I have a Doom3 ISO and am using 9.04.  How do I mount this with Wine so that I can install it without having to burn the ISO?  I was able to do this with Hardy Heron once.  I installed wine with add/remove programs and added the right pubkey for Jaunty.  Please help!

---

### Post by Vaphell on 2009-11-02
mount that iso to some directory:
**mount myiso.iso /mnt/iso/ -t iso9660 -o loop**

navigate there and open setup.exe (or whatever) with wine from context menu (or use **wine /mnt/iso/setup.exe** command).

---

