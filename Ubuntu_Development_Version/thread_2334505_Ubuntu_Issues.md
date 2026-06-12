---
title: "Ubuntu Issues"
date: 2016-08-20
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2016-08-20
I have installed the daily live Ubuntu Yakkety on my Laptop with switchable AMD graphics card and have run into a few issues. These are issues i found from Trusty Tahr onward that has not been resolved. I would like to report bugs but don't know which packages to tag.

I have been booting with quiet splash enabled on my system but randomly, my Laptop screen becomes garbled and unresponsive. To prevent that, i added the nomodeset flag to the grub file and updated grub. Ever since i did that, my physical keys on keyboard for controlling brightness do not work. I mean, the indicator on my laptop screen keeps reducing the brightness count but the actual brightness remains the same. The brightness settings in system settings also do not work. 
Ever since i enabled nomodeset, my laptop has become very sluggish and the effects look like how they used to be on Unity 2D which was last seen on Ubuntu 12.04 if my memory serves me right.

Is there any way to resolve this? Also, which package(s) should i report the bug against in launchpad?

---

### Post by ventrical on 2016-08-20
Could you check settings and see if you graphics module is llvmpipe?

Thanks..

---

### Post by Smask on 2016-08-20
Isn't nomodeset=no hardware acceleration?
Which graphics card are you using?
AMD dropped 2D support on newer HW and run everything thru 3D, which requires llvmpipe.

---

### Post by ventrical on 2016-08-20
> **Smask said:**
> Isn't nomodeset=no hardware acceleration?
Which graphics card are you using?
AMD dropped 2D support on newer HW and run everything thru 3D, which requires llvmpipe.

If I  am correct if you do not choose nomodeset it will set a generic nouveau driver.  I have ATI card and it will work  without install of AMD or nomodeset. But nomodeset will most usually bring in llvmpipe , which, IMO is a complete  fail.

regards..

---

### Post by ventrical on 2016-08-20
> **Smask said:**
> Isn't nomodeset=no hardware acceleration?
Which graphics card are you using?
AMD dropped 2D support on newer HW and run everything thru 3D, which requires llvmpipe.

I had to experiment with this and you are correct. It will now jockey to llvmpipe with Radeon cards running yakkety. But it still chooses nouveau driver without llvmpipe on trusty.

---

### Post by Smask on 2016-08-20
> **ventrical said:**
> If I  am correct if you do not choose nomodeset it will set a generic nouveau driver.  I have ATI card and it will work  without install of AMD or nomodeset. But nomodeset will most usually bring in llvmpipe , which, IMO is a complete  fail.

regards..

llvmpipe=2D emulation on 3D hardware. So nomodeset runs the graphics in software emulator mode and running llvmpipe on top of that...

Me, I'm using AMD card on all my boxes here and running acceleration via Xorg to skip as much of hardware hassles as possible. I have one laptop equipped with an Kabini APU and I think it's using llvmpipe.

---

### Post by Smask on 2016-08-20
> **krishnan t s said:**
> Is there any way to resolve this? Also, which package(s) should i report the bug against in launchpad?


Ask on the Phoronix forum. Several AMD driver guys post on there. There might be a 10 posts rule still active, can't remember.

---

### Post by krishnan t s on 2016-08-23
Thanks for the replies. I was stuck in a place with no internet so i saw your posts just now :)

In nomodeset, the graphics module is llvmpipe. I have a dual AMD graphics(APU A10 quad core.. not sure about the graphics card series.. could be anywhere between 5000-8000). Under quiet splash its using the radeon driver as usual but all of a sudden it gives a garbled screen. Under nomodeset, as of now, i'm getting a semi-smooth experience(still not fluid but getting very marginally better with each reboot) but my brightness controls do not work. Also, i lost my nm-applet with an update. If i launch it from the terminal, i'm getting the nm-applet. Anyway to enable it permanently? Tried adding it manually to the startup applications but it does not work.

Also, i'll give try on phoronix later today though i dont have any account on that site :)
Thanks a lot for your replies.

---

### Post by krishnan t s on 2016-08-29
The latest updates seems to have solved the issues. I'm no longer in nomodeset and my network mamnager is back in the top panel. My laptop has not crashed after using it for 7 hours straight :)
Cheers and thanks for all your replies :)

---

