---
title: "&quot;can not display...&quot; on UbuntuStudio 9.10"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by damu on 2009-11-18
Hi,

I did a fresh install of UbuntuStudio 9.10 on a desktop in a school to set up a sound studio for them, and introduce the school to Ubuntu (with the plan to install it on notebooks, etc.)

On first boot, after the splash screen (which doesn't disply properly...obvious wrong resolution of screen), I get a black screen with the message :
cannot display 
maximum resolution is: 1280*1024

I tried to access the safe mode boot by clicking the 'Esc' key at boot, but I don't seem to be able to access grub...it goes straight to the boot splash screen...

what do you think, I could try next?

Thanks

---

### Post by trulan on 2009-11-18
That sounds like the monitor is generating that message, due to the computer putting out too high of a resolution.  It's an LCD monitor, right?  Do you have an old CRT monitor you can plug in so you can see what the computer is doing?  They usually have higher resolution.

Otherwise, you're going to need to access the file system and manually set the screen resolution, or select a different video driver, by editing xorg.conf (which probably doesn't even exist so you'll have to create a new one).  You can either do this by booting into recovery mode (you'll need to get to the grub menu to do that) or by booting off a live CD and 'chroot'ing or something like that.

Honestly, I think the easiest fix would be to hook up a monitor that supports higher resolution, such as a nice old 17" or bigger CRT (or boat anchor if you prefer ;) ).  Then you can at least see what you are doing and have a better interface to adjust the resolution to 1280x1024 so the original monitor works.

Be aware that Ubuntu will always select the highest resolution possible unless you specify otherwise in xorg.conf.  Apparently it isn't detecting your monitor properly and is setting the resolution too high.

---

### Post by damu on 2009-11-19
thanks Trulan...I tried to access grub but for some reason couldn't manage to at boot.

I will check if the school has another monitor when I go back there as it would be the easiest solution.
If they don't, I might take the ' 64studio beta3' route which is based on Ubuntu anyway, or install plain ubuntu (never had this problem with plain ubuntu and can test with live cd) and install the 'Studio' package on top.

---

### Post by gorgon on 2009-11-19
hi there,

if you are able to access grub, try editing grub at startup:
press 'e' to edit, then go to the line saying 'kernel', and add 'vga=791' to the end.

maybe you can enter grub by hammering the 'esc' key like mad on startup..;)

good luck

---

