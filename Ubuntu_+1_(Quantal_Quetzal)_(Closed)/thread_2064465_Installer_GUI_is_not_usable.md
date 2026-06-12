---
title: "Installer GUI is not usable"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by The Cog on 2012-09-29
Is there a "safe mode" or similar in the installer? I'm trying to install Xubuntu 12.10 (x86) and can't get to a working GUI. I get a very nice cool blue looking XFCE splash screen for a while, then that gies away and I get a very unwell looking pattern on the screen that just sticks that way. See attached image.

Ctrl-Alt-F1 gets me a console where I can see error messages like this streaming past...
[drm] nouveau 0000:05:000: PFIFO_CACHE_ERROR - ch 2/2 Mthd 0x860 Data xxxxxx
the data is changing constantly.
My video card is: VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2)

I normally use the alternate installer (bomb-proof reliable), but they've decided not to make one this time, so I'm a bit stuck.

---

### Post by bird1500 on 2012-09-29
I think this is a nouveau driver issue for (all?) video cards released after the GeForce 8-9 series.
Last time I checked with a daily iso after beta1 the Quantal installer would still freeze completely before showing the GUI while using GeForce 560Ti, but when I switched to the older GeForce 7600GT it all went smooth.

Bottom line, Canonical won't likely fix it unless upstream Mesa 9.0 fixes it. Btw, mesa 8.x didn't have this problem.

So the easy fix is: buy a (cheap & used) GeForce 9600 or even older 7600GT video card for like 20$ and use that to install Ubuntu and the Nvidia driver, then shutdown, put your newer video card and you're done.

---

### Post by The Cog on 2012-09-29
Well, that really is a proctalgia. 

Having to swap video cards just to run an installer is plain stupid as well as inconvenient. I presume it also means that you can't use the installer CD as a rescue CD any more, either.

---

### Post by sacridex on 2012-09-29
Well, I have a 9600gt and the same issue appears! ;)
But I was able to avoid it (with normal Ubuntu though), I pressed tab then enter or something, so it switched to the test Ubuntu button. Then the live mode was started, which appearently worked fine for me.
After installation, I had huge graphic issues too, but I just used tty1 to install the nvidia driver and rebooted.
Maybe that works for you too. Just try some tab + enter combinations, til you load into the live mode. ;)

---

### Post by BigSilly on 2012-09-29
> **bird1500 said:**
> 
So the easy fix is: buy a (cheap & used) GeForce 9600 or even older 7600GT video card for like 20$ and use that to install Ubuntu and the Nvidia driver, then shutdown, put your newer video card and you're done.

Well actually a much much easier fix is to just delete the words 'splash' from the boot options. Make sure you tick the box to download all third party drivers etc when you install, so you get the Nvidia driver rather than Nouveau.

I have a 9800GT. I'm not buying a new card! But yes I do get this issue.

---

### Post by Elfy on 2012-09-29
Did you try using nomodeset from the F6 options at boot ?

---

### Post by 2F4U on 2012-09-29
Certainly not of much help, but there is a bug report for a problem reported in 12.10 that looks similar to yours:

[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1039125](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1039125)

The bug report has three workarounds in it, which you may wish to try.

---

### Post by The Cog on 2012-09-29
Success!

As sacridex suggested, I tried pressing Tab as it was booting (a couple of icons of perhaps a keyboard and a man) and then guessed at F6 (Other options) and enabled nomodeset. This did the trick, and I'm now posting from the live CD. I see that Elfy already knew of this work-round, and I guess it is a way of implementing workround 3 that 2F4U linked.

I must say that it looks very nice, just judging by the live CD. I'll get on with installing now. It seems crisper, somehow.

Thanks again everyone for pitching in and helping.

---

### Post by kaldor on 2012-09-29
GTS 450 here and no issues. Just for the record :P

---

