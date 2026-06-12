---
title: "pangolin performance 6 video issues after clean install"
date: 2009-12-06
forum: System76 Support
---

### Post by eternal_sage on 2009-12-06
ok, so my wife really needs windows in some very rare occasions (plus it makes the occasional gaming session much easier), so i set about putting my shiny new copy of windows 7 (super great discount through my college for being a comp sci major :D) and i really badly botched the grub reinstall (i really hate the new grub, btw), so i ended up having to do a complete reinstall to get everything straightened out. now everything is working like a charm with one very important exception... my video card.

i've gotten the system76 driver, ran it, and got everything back to its proper settings (got this issue before that as well as well, just to be thorough, but after driver hokey pokey i've found it doesn't matter). however, when i install the restricted drivers for my card (the nvidia ones that ubuntu thrusts at me) they install just fine and then on reboot the screen is subdivided into 6 little screens(!?) and i can't even fix it running the settings command for the nvidia driver.

if someone could clue me in on what i've messed up and maybe how to fix, i'd be grateful. thanks guys!

---

### Post by thomasaaron on 2009-12-07
NOTE: THIS IS *ONLY* FOR PANP6 USERS WHO EXPERIENCE THIS PROBLEM.

I've attached an xorg.conf to this thread. Please download it and run this command...

sudo cp Downloads/xorg.txt /etc/X11/xorg.conf

Then reboot.

---

### Post by eternal_sage on 2009-12-07
thanks! unfortunately its giving me an error saying that xorg.conf is invalid when i try to install the new driver. thanks for your help.

---

### Post by thomasaaron on 2009-12-07
Try this...

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then install your hardware driver via System > Admin > Hardware Drivers.

Then run...

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Then reboot.

---

### Post by eternal_sage on 2009-12-07
you the man! lol

its working like a charm. thank you very much for your quick replies!

---

