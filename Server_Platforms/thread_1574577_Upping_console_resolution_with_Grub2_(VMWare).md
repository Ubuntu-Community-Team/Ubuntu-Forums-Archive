---
title: "Upping console resolution with Grub2? (VMWare)"
date: 2010-09-14
forum: Server Platforms
---

### Post by Xiol on 2010-09-14
Hello,

I've spent the last 30 minutes exercising my Google-fu and I've managed to break it once and not get it working at all.

Back in the days of Grub1 all you had to do was add a vga=xxx line and there you go, increased console resolution with about as much effort as making a cup of coffee.

Grub2 seems to have made things complex for the sake of it. Seriously, what is the replacement procedure for upping the console resolution?

I've tried editing 00_header as specified on other sites and all that did was break my system. Having fixed that issue and returned back to a 640x480 console I'm none the wiser.

So far I have:

* Added gfxpayload=true to the GRUB_CMDLINE_LINUX option in /etc/default/grub
* Uncommented and adjusted GRUB_GFXMODE
* Tried to edit the /etc/grub.d/00_header file to add gfxpayload=keep and tried that with insmod vbe as pointed out elsewhere (this broke my system, black screen)
* Added GRUB_GFXPAYLOAD_LINUX="keep" to /etc/default/grub, this also broke my system with a black screen as above.

And various combinations thereof.

This is all happening inside a VMWare VM, however I will shortly be deploying 10.04 to a physical machine as well and I want to do the same on there.

---

