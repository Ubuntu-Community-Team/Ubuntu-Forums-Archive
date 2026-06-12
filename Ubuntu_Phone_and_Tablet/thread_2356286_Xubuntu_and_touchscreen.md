---
title: "Xubuntu and touchscreen"
date: 2017-03-21
forum: Ubuntu Phone and Tablet
---

### Post by Tim474 on 2017-03-21
I have a touchscreen laptop and Xubuntu 16.10 installed. By default  there is no support of multi-finger gestures. Only left mouse button  click when tapping. I install touchegg and touchegg-gce. After it  multi-finger gestures were enabled, but left mouse button click  emulation doesn't work if I click on window header. I can't move window  and use buttons in up-right corner. If I create a gesture in  touchegg-gce that emulates LMB click on one finger tap, it emulates two  clicks.
  How to fix it? Now I want to work with touchscreen as it works  without touchegg (LMB click on any place of screen) but with 2 finger  scrolling and RMB emulation with 2 finger tapping.

---

### Post by Tim474 on 2017-03-22
Please help me. Scrolling with touch screen and emulation of RMB is obvious functionality. But it doesnt' work in both ubuntu (unity), ubuntu-gnome and xubuntu on certified device.

---

### Post by Tim474 on 2017-03-22
Now I want to disable LMB click when I touch the touchscreen (only use it for cursor moving), but I can't do it. xinput set-button-map <number of toucscreen> 0 0 0 0 0 0 0 0 0 0 0 0  doesn't help. If I execute xinput query-state <number of touchscreen> when I touch it, xinput writes that all buttons are up.

But I can fully disable touchscreen with xinput --disable <number of toucscreen>

---

### Post by dtarrant on 2017-03-24
I use the Aquaris M10 on a daily basis. The operating system is Ubuntu Touch which is based on Ubuntu 15.04. Apart from a fair number of touch-optimised tablet apps, the M10 can also run in desktop mode if you connect a bluetooth mouse and keyboard. The desktop apps include Firefox, LibreOffice (Writer, Calc, Draw, Impress, etc), Gimp and Gedit. Updates are provided quite frequently. In tablet mode, I access the following sites without any problem: Office 365 Web App (webmail); Facebook; Youtube; BBC News; BBC Weather; Distrowatch; OMG Ubuntu; Reddit; Slashdot; The Register; Here Maps; uNav; and many more.

Ubuntu Touch's big feature is Convergence. It offers both tablet and desktop capability. It isn't yet as polished as ipad or android. However it is perfectly usable and great fun. There are also powerful tools available to enable you to write your own apps.

Another important feature is that it has a micro sd card slot which means that for a modest outlay you can increase the memory capacity by 64GB.

My M10 is definitely not for sale. I am confident that it will continue to get better. It's an exciting ride!

---

### Post by Tim474 on 2017-03-26
I don't ask about Ubuntu touch and touch-optimized applications. I have a 2-in-1 laptop and want to use it mostly in laptop mode and use tablet mode as a bonus, but in with all aplications.

---

