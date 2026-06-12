---
title: "New battery"
date: 2008-08-05
forum: Windows
---

### Post by Sub101 on 2008-08-05
Hello, i got a new extended battery today for my HP DV2699ea. It works fine in Ubuntu with no problems. 

In Vista however it will not allow boot. The power cuts out completely until I remove the battery and reinsert. Pressing the power button boots into grub where if i select Vista again the problem repeats itself. Also if i boot into Vista on AC then remove AC it works fine again. 
 
I think the problem is that the boot takes a lot of power and maybe the battery is not up to it? Just curious as to whether there is maybe a way around this. I don't actually use Vista much but I like knowing it is available if i need it.

Thanks for your help

EDIT: Turns out booting in Ubuntu is also a problem?

---

### Post by fiddledd on 2008-08-06
It sounds like the battery is faulty. If it's charged and there's not enough power it's the battery and not Ubuntu or Vista.
Were there any problems booting with the old battery?

---

### Post by abgemacht on 2008-08-06
This is a hardware and not an OS problem.  Does it always boot fine with AC?  If so, it's most likely the battery and not some internal wiring (which is good).

First, check to see if that battery has any recalls.  Depending on how new it is, you should be able to get a replacement.

---

### Post by Sub101 on 2008-08-06
The thing is that once booted into Vista/Ubuntu it works fine its just the booting itself. And no no problems at all with booting on my old battery or from AC. So it looks like the only option is another new battery?

---

### Post by fiddledd on 2008-08-06
> **Sub101 said:**
> The thing is that once booted into Vista/Ubuntu it works fine its just the booting itself. And no no problems at all with booting on my old battery or from AC. So it looks like the only option is another new battery?

You've answered your own question really. If there was no problem with the old battery and there is now, it can only really be a faulty battery. Unless there's something else different with hardware. If possible I would try the battery on a compatible Laptop first, but I think you need a replacement. If it was one OS, then that might have been the problem, but both OSes at the same time has to hardware, and in this case, the battery.

---

### Post by ARhere on 2008-08-07
I _strongly_, disagree that the problem is with the physical battery from what I have heard.  You already said,
> It works fine in Ubuntu with no problems.  so you know the new battery can handle the larger load of booting up.  Booting up a different OS does not change hardware, so I would immediately suspect there is something wrong with the software interface to the battery.

All laptop Li-Ion batteries have a safety and monitoring circuit built into them.  In order to keep from damaging the battery, a Li-Ion protection circuit will cut off the battery if the voltage of the cell(s) drops below 3.0 volts or is greater then 4.3 volts.  There is also a charging circuit in the laptop (*sometimes in the battery as well*) that will also monitor battery levels and current draw and cut off the cells if it detects something wrong.  Your operating system will know it's battery level+status through a driver to this monitoring hardware and if misreported, can cause odd behaivor.  This is usually a generic ACPI driver built into Windows but because it is a laptop, it is very possible the driver is custom from the laptop vendor.

I am _still_ reading about a lot of bugs with hardware that was designed for the Windows XP/2000 days being used with Vista.  I would honestly Google for a bug report on your battery model + Vista and see what you get.  Post your battery S/N: and you laptop make/number and I will help you look.

The short story is, if your battery does not cut out under a strong load with Ubuntu, then it is fine and you have a driver issue.  If you really want to be sure the battery is ok, run your laptop with the new battery while using it heavily, anything with a motor.  For example try watching a DVD on Ubuntu without the AC plugged in, and see how long it lasts.  If you only get 10 minutes on a full charge, then I could be wrong and you have a bad battery.

-AR

---

### Post by fiddledd on 2008-08-07
> **ARhere said:**
> I _strongly_, disagree that the problem is with the physical battery from what I have heard.  You already said,
 so you know the new battery can handle the larger load of booting up.  Booting up a different OS does not change hardware, so I would immediately suspect there is something wrong with the software interface to the battery.

All laptop Li-Ion batteries have a safety and monitoring circuit built into them.  In order to keep from damaging the battery, a Li-Ion protection circuit will cut off the battery if the voltage of the cell(s) drops below 3.0 volts or is greater then 4.3 volts.  There is also a charging circuit in the laptop (*sometimes in the battery as well*) that will also monitor battery levels and current draw and cut off the cells if it detects something wrong.  Your operating system will know it's battery level+status through a driver to this monitoring hardware and if misreported, can cause odd behaivor.  This is usually a generic ACPI driver built into Windows but because it is a laptop, it is very possible the driver is custom from the laptop vendor.

I am _still_ reading about a lot of bugs with hardware that was designed for the Windows XP/2000 days being used with Vista.  I would honestly Google for a bug report on your battery model + Vista and see what you get.  Post your battery S/N: and you laptop make/number and I will help you look.

The short story is, if your battery does not cut out under a strong load with Ubuntu, then it is fine and you have a driver issue.  If you really want to be sure the battery is ok, run your laptop with the new battery while using it heavily, anything with a motor.  For example try watching a DVD on Ubuntu without the AC plugged in, and see how long it lasts.  If you only get 10 minutes on a full charge, then I could be wrong and you have a bad battery.

-AR

I think you should read the OP again, especially the EDIT.

---

### Post by ARhere on 2008-08-07
> **fiddledd said:**
> I think you should read the OP again, especially the EDIT.

Right ... did not see the edit ... damn italics.  
Thanks fiddledd.:oops: 

Well, if it cuts off no matter what OS is used, then it could be a bad battery, this is how you find out.

Boot the laptop anyway you can with the AC adapter and battery plugged in and let the battery fully charge.  Turn off power management in the laptop, start a movie in Vista/Ubuntu/whatever, and unplug the AC cord.  > if i boot into Vista on AC then remove AC it works fine again. 
If the laptop plays for a short while, under 10 minutes and then croaks, you can safely assume the battery has formed a high impedance and is bad.  If it play for a nice long time, whatever is expected with the old battery, then my original thought is still possible.

Try this and let us know.
-AR

---

