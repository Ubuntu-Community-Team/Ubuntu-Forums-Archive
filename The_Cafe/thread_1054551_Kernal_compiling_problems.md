---
title: "Kernal compiling problems"
date: 2009-01-29
forum: The Cafe
---

### Post by Hugh Mulqueen on 2009-01-29
right i dont know if im in the right thread here??, 
But i have been trying for the past 7 hours to compile, patch and install the latest kernel from kernel.org. 
To be more specific Linux-2.6.28-rc2-mm1. 
I think it's about to install when i get this:

  [FONT="System"]INSTALL sound/soc/snd-soc-core.ko
  INSTALL sound/sound_firmware.ko
  INSTALL sound/soundcore.ko
  INSTALL sound/synth/emux/snd-emux-synth.ko
  INSTALL sound/synth/snd-util-mem.ko
  INSTALL sound/usb/caiaq/snd-usb-caiaq.ko
  INSTALL sound/usb/snd-usb-audio.ko
  INSTALL sound/usb/snd-usb-lib.ko
  INSTALL sound/usb/usx2y/snd-usb-usx2y.ko
  DEPMOD  2.6.28-rc2-mm1[/FONT]

and it just stays like that for ages???
is it doing anything??

Any help would be much appreciated!!.

---

### Post by cardinals_fan on 2009-01-29
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Hugh Mulqueen on 2009-01-29
Thanks very much for the link...
I have the following files already:
linux-2.6.27.tar.bz2
patch-2.6.28-rc2.bz2
2.6.28-rc2-mm1.bz2

Is there any problems with the combination above?

I did successfully run make when I applied the patches so i dont know.....

---

### Post by cardinals_fan on 2009-01-29
> **Hugh Mulqueen said:**
> Thanks very much for the link...
I have the following files already:
linux-2.6.27.tar.bz2
patch-2.6.28-rc2.bz2
2.6.28-rc2-mm1.bz2

Is there any problems with the combination above?

I did successfully run make when I applied the patches so i dont know.....
I generally compile my kernel with the kernel sources provided by my distro.  My only recommendation is to follow that guide to the letter.

---

### Post by Hugh Mulqueen on 2009-01-29
Tahnks man for the advice..

---

