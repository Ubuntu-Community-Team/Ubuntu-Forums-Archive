---
title: "My computer tried to boot from my sansa fuze!"
date: 2009-05-04
forum: The Cafe
---

### Post by dragos240 on 2009-05-04
This is so interesting! Last night I plugged in my fuze because the battery was low, and then it was 9. I shut down. About 20 minutes ago, I tried to boot up, and the bios wouldn't load for about 10 minutes. And then a few more tries of the same result, I was dumbstruck! And then I unplugged my sansa, and powered down, it booted! I tried it a few more times. The wierdest thing though is, even though I have my computer set to boot from a USB before a hard drive OR disk, when I insert a normal usb stick with no boot parameters, or anything, my bios skipps it. This leading to the assumption that my bios tried to boot from my sansa. Why would this be? And how?

---

### Post by yabbadabbadont on 2009-05-04
Your sansa apparently has a valid MBR on it while your normal usb stick doesn't.  So the bios loaded the MBR from the sansa and transferred execution to it.  However, the code contained therein would only be valid if the sansa is the hardware being booted, hence the lockup.

---

### Post by dragos240 on 2009-05-04
Huh. Interesting. It would be interesting if it ACTUALLY booted wouldn't it?

---

### Post by DeadSuperHero on 2009-05-04
I wonder, could you put Coreboot on a Sansa and test-boot it? :shock:

---

### Post by Brainy142 on 2009-05-04
My psp is recognised as a wait for it..... a disk lol:lolflag:.

---

### Post by OutOfReach on 2009-05-04
This exact thing also happens with my iPod nano, I plug it in to recharge, then I reboot (w/o taking the iPod out) then the bios screen comes up as usual...then a blank screen with only a cursor comes up. The first time this happened I thought I messed up my computer, heh, until I took out the iPod I realized what it was trying to do...

---

### Post by Brainy142 on 2009-05-04
But my psp is recognized as an ACTUAL CD?????

---

### Post by Redache on 2009-05-04
>  		But my psp is recognized as an ACTUAL CD????? 	

What? if you mean it's recognised as a Removable Disk then no it's not a CD. The Computer is picking it up as a storage device, it won't specify what Device but it will just call it a Removable Disk. 

If it was picking it up as an actual 700Mb CD then something is seriously wrong. I can't even imagine how that would happen.

My Computer sometimes attempts a boot from USB devices if I leave them Plugged in, I think its just that some devices have some form of MBR to actually load the device and the BIOS picks up on it but it obviously can't execute the code.

---

### Post by days_of_ruin on 2009-05-04
> **dragos240 said:**
> This is so interesting! Last night I plugged in my fuze because the battery was low, and then it was 9. I shut down. About 20 minutes ago, I tried to boot up, and the bios wouldn't load for about 10 minutes. And then a few more tries of the same result, I was dumbstruck! And then I unplugged my sansa, and powered down, it booted! I tried it a few more times. The wierdest thing though is, even though I have my computer set to boot from a USB before a hard drive OR disk, when I insert a normal usb stick with no boot parameters, or anything, my bios skipps it. This leading to the assumption that my bios tried to boot from my sansa. Why would this be? And how?

Thats strange because a sansa c250 prevents my computer from booting.
But AFAIK my sansa fuze does not prevent it from booting.

---

