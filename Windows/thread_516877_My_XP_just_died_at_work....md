---
title: "My XP just died at work..."
date: 2007-08-03
forum: Windows
---

### Post by klato on 2007-08-03
So here I am at work, and my comp had completely locked up.  I had to do a hard reboot, and when I booted into XP, I got a blue screen of death.  I tried booting into all available options, but nothing worked...always got a blue screen.

The only option that shed any light on it was Safe Mode, which flashed a bunch of text at me, and finally stopped at **agpcpq.sys**

I also tried a system restore, but according to that there is no hard drive in the system (even though it is detected by the bios)!

I had a feisty cd sitting around so I figured I'd boot into that for a bit to at least have a functional system, and it actually worked fine and it detected the hard drive and I was able to browse the contents.  However, now upon doing another boot into ubuntu, it doesn't even want to boot at all, and all I see is a black screen with a spinning cursor.

Does anyone have any idea as to what happened?

Thanks!

---

### Post by smoker on 2007-08-04
could be a couple of things, though because it is affecting both windows and linux now, i would first check the motherboard manufacturers support site of a bios update, and update of the chipset drivers.

also, have a look at this link:
[http://support.microsoft.com/default.aspx?scid=kb;en-us;324764](http://support.microsoft.com/default.aspx?scid=kb;en-us;324764)

best of luck

---

### Post by klato on 2007-08-05
thanks smoker, i'll check it out on monday and report back =)

---

### Post by klato on 2007-08-06
woops...i went to update the bios but turns out the system doesn't have a floppy drive...nor does the motherboard have a connection for one! :(

how does one do the update without a disk?  i tried booting to my usb card but that gave me a "Missing operating system" error (i had copied the files from a bootable floppy)

---

### Post by smoker on 2007-08-07
there should be instructions posted on how to update the bios from a usb if you don't have a floppy, but it probably depends on the motherboard maker, so support may be good or bad!

if have a usb boot option in your bios, you could maybe use winimage to create a bootable usb drive with the bios update. if not, you could make a bootable cd. have a look at these links:
[http://www.winimage.com/winimage.htm](http://www.winimage.com/winimage.htm)
[http://www.nenie.org/misc/flashbootcd.html](http://www.nenie.org/misc/flashbootcd.html)

i used winimage before, though years ago! so i would advise caution and read carefully through each stage.

anyway, best of luck.

---

### Post by klato on 2007-08-08
It turned out I was on crack, and there was a floppy connection.  I've updated the bios, but I still get that blue screen.

Any other ideas?  I'm still searching around on google and such but haven't found any solution =(

---

### Post by EndPerform on 2007-08-08
> **klato said:**
> It turned out I was on crack, and there was a floppy connection.  I've updated the bios, but I still get that blue screen.

Any other ideas?  I'm still searching around on google and such but haven't found any solution =(

See if your motherboard support site has a diagnostic tool you can run from a boot disk.  Or, try pulling out cards (other than video) and see if that helps.  If not, it's either going to be a video card or something on your motherboard.

---

### Post by smoker on 2007-08-08
hi, did you try the resolution on the microsoft link i gave above?

also, if possible, can you post the bsod error message?

---

### Post by klato on 2007-08-10
yup i tried that but it didn't work.  unfortunately, the machine is now gone so i guess we'll never know.

now they've given me a shiny new dell with windows vista home premium ultra championship turbo whatever edition on it...:lolflag:

---

### Post by smoker on 2007-08-10
> **klato said:**
> yup i tried that but it didn't work.  unfortunately, the machine is now gone so i guess we'll never know.

now they've given me a shiny new dell with windows vista home premium ultra championship turbo whatever edition on it...:lolflag:

ah, well, one way to sort the problem!

what happened to the old machine, was it scrapped?

---

### Post by klato on 2007-08-12
the system is now sitting in a closet!  i suppose some day when i have time i´ll go sniffing around in there again to see what i can do with it ;)

thanks for your help though!

---

