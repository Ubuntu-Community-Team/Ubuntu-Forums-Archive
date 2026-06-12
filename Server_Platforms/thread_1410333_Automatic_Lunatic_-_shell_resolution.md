---
title: "Automatic Lunatic - shell resolution"
date: 2010-02-18
forum: Server Platforms
---

### Post by Mirko Scurk on 2010-02-18
I needed Ubuntu server and recklessly picked Karmic. Hardware is some regular 775 mobo with integrated Intel graphics. Monitor is ASUS VH222D. Installation went smoothly but after that problems occurred. Shell is displayed in 1920x1080 resolution and fonts are so small almost unreadable. Grub2 looks OK, standard non-fb and so does few rows of text after loading grub but soon after that framebuffer becomes active. 

dpkg-reconfigure console-setup doesn't mention resolution. Some articles are leading to grub2 gfxmode but none of manuals helped. I just cannot change grub2 menu resolution to anything else than standard console fonts (non-fb). Kernel option vga=XXX is no longer working.

How to lower shell resolution? Why is this automatic???

---

### Post by DrMelon on 2010-02-18
Strange that the shell is in 1080p on an integrated card...

---

### Post by Mirko Scurk on 2010-02-18
Characters was tiny so I checked resolution in monitor menu info. On other computer with K8M890 mobo, integreted via chrome and same monitor after installation there is no framebuffer and characters are huge. Tried some mumbo-jumbo with grub2 gfxmode but there is so many contradictory instructions what to insmode and what to blacklist, to rebuild initram-fs or not to rebuild, to add gfxpayload to 00_header or not to. Seems to me that grub2 is not well prepared and lacks detailed documentation - unnecessary adventure.

---

