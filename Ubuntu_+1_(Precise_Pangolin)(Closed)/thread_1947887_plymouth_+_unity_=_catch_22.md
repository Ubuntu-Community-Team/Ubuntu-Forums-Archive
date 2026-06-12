---
title: "plymouth + unity = catch 22 ?"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mpbb77 on 2012-03-27
To get plymouth space-sunrise fully working (dawning/sunsetting), it seems the only way for me is adding "nomodeset" to the kernel grubline. Adding "video=uvesafb (or vesafb):mode_option=1024x768-24,mtrr=3,scroll=ywrap" works, but actually seems irrelevant to this.

But every configuration I've tried with modesetting disabled through kernel grubline, module loading (either vesafb or uvesafb) in default /etc/initramfs-tools/modules) and blacklisting gives the same result: the system seems to default to a llvmpipe driver (from what I get from glxinfo), which seems to indicate no driver has been loaded even if proc/fb and dmesg seems to tell otherwise.

On the contrary, enabling modeset displays a static plymouth image and the xserver starts fine, always with radeondrmfb at fb0. If I leave the video=etc.. in grubline, the other drivers are a loaded correctly at fb1 or even fb2. If I try to start a session from tty with these fbs, i get a black/transparent screen with cursor and "dri2swapuffers bad drawable" error.

My ghw is an ati x700 m26, 1280x800 screen, on pp beta 2.

So it seems I cannot get both worlds. Do you have any ideas of some mcd mode/driver that could handle it ? It seems like radeondrm is loaded first whatever option, and it is the only one to work perfectly ut I couldn't find it as a standalone module so that I could use nomodeset and load it.

Tx

---

### Post by mpbb77 on 2012-03-27
Ok, I've just found where in the kernel the radeon drm fb is configured and it is marked as a module named ... radeon. I was using radeonfb to load or blacklist alonside uvesafb and vesafb.  So I guess I have to start my tinkering back from scratch

---

