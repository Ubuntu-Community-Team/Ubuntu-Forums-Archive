---
title: "Is My Computer Dying?"
date: 2010-09-07
forum: The Cafe
---

### Post by Mark76 on 2010-09-07
I'm putting this here because I'm not sure whether it's something to do with Ubuntu or not.

Basically I've been experiencing the following two symptoms

Mouse and keyboard freeze and become unresponsive (cursor won't move)

Random self-rebooting.

Anyone know why these things might be happening?

---

### Post by del_diablo on 2010-09-07
Give you computer "the makeover".
That means cleaning it, and upgrading BIOS.

---

### Post by chessnerd on 2010-09-07
Mouse and keyboard freezes can be caused by any number of things. For example, when my computer comes out of standby I can't use the keyboard until I open a new application of some sort and type in it (no, I've never tried to fix it, I just let it go). Without more to go on I have not clue. 

Basic advice - If the mouse and keyboard are wireless, make sure the batteries aren't dying. If they are wired, make sure they are plugged in firmly.

Random self-rebooting? Well, I'm not sure what might cause this.

Basic advice - Run updates to the system, update the computer BIOS. Check the system log to see if there is any reason why it might be shutting down randomly. Make sure everything is plugged in properly.

If none of this works, we'll need more information about when this occurs. If you have no idea, then you might want to back-up your system and reinstall Ubuntu to see if that fixes it.

---

### Post by HermanAB on 2010-09-07
Most computer problems are due to the PSU.  So, take a guess and replace something, then see if it works better.

---

### Post by earthpigg on 2010-09-07
It could be overheating due to not being cleaned in ages.

Physically open it and clean it out with a can of air.

***If you are a smoker and smoke around your computer*** (or if a previous owner did), then you may need to do more. 

Remove the hard drive(s), optical drive(s), Power Supply, CMOS battery, and anything else with moving parts or stored electricity that i missed. Set that stuff aside.

Go purchase some distilled water.

Individually dip each part not mentioned above (motherboard, ram, etc) in the distilled water and gently remove the tar with your fingers.

Set everything out to dry for two weeks.

Reassemble. 

(Yes, I have actually done this. For my mother's computer.)

---

### Post by Lensman on 2010-09-07
> **HermanAB said:**
> Most computer problems are due to the PSU.  So, take a guess and replace something, then see if it works better.

Herman has some good advice. There are any number of reasons that could cause your symptoms, from overheating to bad capacitors, but as a rule of thumb, the stranger the problem is, the more likely it is PSU related.

---

### Post by del_diablo on 2010-09-07
Another tips: Run dmesg after the "locking" has happened.
In the last 10-20 lines, there tends to be quite nasty and obvious things.

---

### Post by Johnsie on 2010-09-07
Sounds like an overheating issue. Clean out the dust and check to make sure the fan is working properly. If there are any broken blades on the fan then replace it. Also, replace the PSU and check that the memory is inserted properly.

Are the reboots occurring in Windows, Ubuntu or both? If it's Windows XP then do the following:

Right click my computer
Click Properties
Click Advanced
Startup and Security -> Settings
Uncheck the 'restart automatically' box


This might stop the reboots but wont fix the underlying problem.

---

### Post by lisati on 2010-09-07
My first thought was the possibility of overheating related problems. A cleaning won't hurt. My laptop gets grubby quickly, and my being a smoker doesn't help.

---

### Post by cascade9 on 2010-09-07
> **del_diablo said:**
> Give you computer "the makeover".
That means cleaning it, and upgrading BIOS.

+1. That would be my first plan of attack, well before buying a new power supply unit, etc..


> **earthpigg said:**
> It could be overheating due to not being cleaned in ages.

Physically open it and clean it out with a can of air.

***If you are a smoker and smoke around your computer*** (or if a previous owner did), then you may need to do more. 

Remove the hard drive(s), optical drive(s), Power Supply, CMOS battery, and anything else with moving parts or stored electricity that i missed. Set that stuff aside.

Go purchase some distilled water.

Individually dip each part not mentioned above (motherboard, ram, etc) in the distilled water and gently remove the tar with your fingers.

Set everything out to dry for two weeks.

Reassemble. 

(Yes, I have actually done this. For my mother's computer.)

I've done this on computers that didnt have a smoker anywhere near them. Mainly due to 'dust bunnies' getting truned into 'mud bunnies' (or even concrete) thanks to high humidty. 

BTW, I add a little metho to the mix. Makes the gunk a bit softer. Works even better with tar.

---

### Post by BkkBonanza on 2010-09-07
To paraphrase Fight Club,

"All computers are dieing in the Sylvia Plath sense".

---

### Post by msandoy on 2010-09-07
This really sounds like a PSU problem. Go into BIOS, and check the actual readings of 12, 5 and 3.3 volts from your PSU. if any of them are low, 5% or more, this is your problem. Just to rule out overheating, check cpu temperatur while you are in BIOS, this is sometimes wrongly reported to the OS. Over 50°C for AMD or over 60°C for Intel at idle is very high, and will cause troubble at loaded condition. Then it's just a matter of replacing the paste between the cooler and cpu.

---

### Post by CharlesA on 2010-09-07
> **msandoy said:**
> This really sounds like a PSU problem. Go into BIOS, and check the actual readings of 12, 5 and 3.3 volts from your PSU. if any of them are low, 5% or more, this is your problem. Just to rule out overheating, check cpu temperatur while you are in BIOS, this is sometimes wrongly reported to the OS. Over 50°C for AMD or over 60°C for Intel at idle is very high, and will cause troubble at loaded condition. Then it's just a matter of replacing the paste between the cooler and cpu.

Heh, never trusted those voltage reading, as they've been (slightly) off on every machine I've owned, so I verify with a multimeter.

My bet is it was overheating.

---

### Post by Mark76 on 2010-09-07
> **del_diablo said:**
> Give you computer "the makeover".
That means cleaning it, and upgrading BIOS.

I have nothing to clean it with (other than a good shake) and I have no idea what to do with the BIOS.

---

### Post by cascade9 on 2010-09-07
> **Mark76 said:**
> I have nothing to clean it with (other than a good shake) and I have no idea what to do with the BIOS.

'Cans of air' (a 'gas duster') should be fairly cheap, and avaible at a fair few places. 

I dont bother with cans of air in mosts cases myself, a cotton bud dipped in metho will do the job. If the heatsink is really filthy, I tend to pull it off, remove the fan, and give it a good scrub in hot water, dry it out, and replace it. To do that you would need some new thermal paste......its not a job that everybody would want to do though. However, its probably a good idea to do that, after a few years thermal paste can go hard and dry, then it acts more like a blanket than helping the heat transfer to the heatsink. 

As for the BIOS, try getting the dust bunnies out before you go updating the BIOS IMO.

---

### Post by neu5eeCh on 2010-09-07
> **Mark76 said:**
>  Mouse and keyboard freeze and become unresponsive (cursor won't move)

Random self-rebooting.

Anyone know why these things might be happening?

Probably your hard drive going bad.

---

### Post by Johnsie on 2010-09-07
Some of those cans of air randomly squirt out a liquid on some occasions. We use them for our keyboards in work. The liquid dries pretty quick but I have no idea what is in it. Could possibly damage hardware?

---

### Post by LowSky on 2010-09-07
> **Johnsie said:**
> Some of those cans of air randomly squirt out a liquid on some occasions. We use them for our keyboards in work. The liquid dries pretty quick but I have no idea what is in it. Could possibly damage hardware?

no, but it can cause frostbite to your skin.

---

### Post by sydbat on 2010-09-07
Cans of air? What a [s]scam[/s] waste of money. 

Just shut the box down, unplug it (if it is a laptop, take the battery out too), open it up (again, if a laptop, open as many areas as you can without completely disassembling it) and vacuum it out (use the crevice tool). I've been doing this for over a decade, every 6 months (on my own AND client computers) and have never had a problem.

---

### Post by cariboo on 2010-09-07
If you are going to use a vacuum cleaner on your computer, make sure the thing is grounded properly, I've seen big fat static sparks jump from the tip of the vacuum cleaner to the circuit board, destroying it. Canned air is much safer.

The liquid you see coming out is just freon, it won't hurt anything.

---

### Post by red_Marvin on 2010-09-07
> **cariboo907 said:**
> The liquid you see coming out is just freon, it won't hurt anything.

Except the ozone layer... They still use freon? I thought it had changed to propane or some less dangerous gas.

---

### Post by msandoy on 2010-09-07
Well, the damaging effect on the ozone layer depends on the type of freon used. R-22 and R-12 have now been totally banned all over the world, and the less damaging replacements are R-134A, R-417A and R-404A.
To save the environment, use the plastic suction pipe on your vacuum cleaner to prevent sparks.

---

### Post by Old_Grey_Wolf on 2010-09-07
> **msandoy said:**
> 
To save the environment, use the plastic suction pipe on your vacuum cleaner to prevent sparks.

The plastic is the cause of the problem. Plastic is non-conductive; therefore, the static charge from the air movement has no pace to go until the plastic is brought into close proximity to something conductive. That conductive material could be you CPU, GPU, or RAM.

---

### Post by barney385 on 2010-09-07
> **Old_Gray_Wolf said:**
> The plastic is the cause of the problem. Plastic is non-conductive; therefore, the static charge from the air movement has no pace to go until the plastic is brought into close proximity to something conductive. That conductive material could be you CPU, GPU, or RAM.

Absolutely. That's the same reason you never put a can of gas in the bed of a truck with a plastic bed liner.

---

