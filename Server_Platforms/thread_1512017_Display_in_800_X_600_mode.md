---
title: "Display in 800 X 600 mode"
date: 2010-06-17
forum: Server Platforms
---

### Post by Jya Dad on 2010-06-17
I am running 10.04 on a home server. Normally run as a headless server, but sometimes want to attach an old CRT monitor. The monitor only has a resolution of 800 x 600.
 
When using the monitor, the bios splashes fine, then Ubuntu starts and the screen goes to color bars. I use PuTTY from a desktop machine and can see the server running. 
 
Not a big deal, but a pain to move a newer monitor to the server when I have a hardware change.
 
Setup:
10.04 server (SSH & Samba only)
x86 with 384M ram
1.5 TB raid 1

---

### Post by Southcross on 2010-06-17
interesting... sounds more like a video/driver issue, as if your not runing a GUI, nothing will generate "color bars"
the "text mode" interface is  approx 24-30 lines x 80 columns (off the top of my head)... this is approx 320x240 resolution (again, off the top of my head).  Heck, it should run off the old fashioned "Green Screen" monitors

---

### Post by Jya Dad on 2010-06-18
1) "Color bars" is the error mode of the monitor when the resolution is too high for it to handle. (Actually using a VGA to TV convertor that works with an old XP machine)
2) When using a newer monitor the "text mode" interface looks to be 1024 x 768. This resolution is probably the default of the ATI on-board graphics.
(Forces me to use my bi-focals to read the text.)

---

