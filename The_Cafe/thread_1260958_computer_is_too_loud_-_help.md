---
title: "computer is too loud - help"
date: 2009-09-08
forum: The Cafe
---

### Post by bionnaki on 2009-09-08
the CPU fan on my desktop never turns off -- it just runs at full speed from the moment the computer is switched on and never varies like it used to in regards to processing tasks. I know it's the CPU fan and not the power supply fan because I unplugged the CPU fan from the motherboard and that particular sound was gone.

obviously, I cannot keep the fan unplugged...but the sound is driving me nuts. my computer has been running like this for 3 months now, but now that I've moved the computer into my bedroom has it been really noticed. I'd rather find a solution other than move the computer into another room. 

what could be the cause of this problem? I figure it's either a problem with the fan itself, the PSU needs to be replaced, or the motherboard is messed up. the bios is up-to-date (I do not have any fan options in the bios, as far as I can tell). 

any input would be greatly appreciated.

---

### Post by Screwdriver0815 on 2009-09-08
so if I understand you right, the fan has varied its speed in former times according to the load but now it doesn't do it anymore?

have you checked, if the cooling rib thing on the CPU is clean? Because it collects dust between the ribs and then oviously the heat transition is no more like it should be. This causes the fan running in fullspeed all the time.

cleaning this cooler also makes the fan noise lower because the dust causes the fan running in this dirty environment which causes noise.

Otherwise: get used to it! :D I know a guy who has a big Tower with 5 harddisks and 4 or 5 fans in it. This thing sounds like a turboprop engine... and this guy sleeps next to it (the machine is never turned off). :lolflag:

BTW: harddisks, if they are not mounted properly also cause noise, because the vibrations go into the computer housing

---

### Post by Paqman on 2009-09-08
Could be anything, BIOS, motherboard, the fan itself, cooling in general.

How hot does the CPU actually run? If it's nice and cool then you're looking at a fault somewhere, if it's hot you probably just need to do a bit of maintenance.

---

### Post by bionnaki on 2009-09-08
thanks for the replies

@Screwdriver0815: yeah, before the fan would speed up and slow down depending on what I was running...or would run at full-speed when booting and then slow down once everything was loaded. I'll try to clean the fan/sink - it is very dusty.

@Paqman: according to acpi -t, my temps are: *Thermal 0: ok, 34.5 degrees C* and that's with the fan plugged in...

---

### Post by Paqman on 2009-09-08
That's nice and cool. Sounds like the PWM (ie: variable speed control) of the fan is knackered then. That could be BIOS, mobo, fan cable, or the fan itself. Double-check your BIOS for fan speed control options, they should be in there. Sometimes they're called weird names like Q-Fan. Wouldn't hurt to visually inspect the fan cable and it's connectors, too.

---

### Post by The Real Dave on 2009-09-08
I say definately take apart heatsink and clean that sucker out, its probably clogged up with dust. I had a similar problem with my computer a while back, a 3Ghz PIV.

It used idle at 58C and spike straight to 65C after 3 seconds. I bought a can of compressed air and cleaned out the heatsink for the first time in its three year life. The amount of dust that came out was ridiclious. 

The CPU fan used run maxed out 4500rpm, the thing sounded like a plane trying to take off. After the cleaning, temp dropped to 40C, fan to 1K rpm. Would rise to 45C @ 1700rpm under load for an hour. 

After messing around with PWMconfig (seat of the pants job really, trial and error), I managed to find a setup I like, CPU idles at 28C @ 2k rpm, and never goes above 35C @ 2700rpm. Its kinda noisy, but I prefer it cold :)

EDIT: after reading the thread again, I agree with Paqman, it does sound like your PWM is bust. If it was a dust problem, your temps would be higher. Still, its worth keeping your heatsink clean anyway :D

---

### Post by matt79 on 2009-09-08
I would also try cleaning the heatsink for sure. Thats what I do when people tell me their computers are loud.

---

### Post by aaaantoine on 2009-09-08
If the fan sounds bad, you can try replacing the heatsink/fan combo with a reputedly quieter solution.  If you have enough room in your case, you can even get an extra large heatsink and get rid of the fan.

But yeah, try cleaning the current one first before you do that.

---

### Post by Onesimus on 2009-09-08
What is your system spec. Laptop / Desktop, etc, etc.

If this is given help could be more focussed.

I have a Dell laptop and have to install gkrellm and ik8utils - maybe there is something similar for your rig.

---

### Post by bionnaki on 2009-09-08
thanks everyone.

I cleaned out the heatsink/fan -- there was a massive amount of dust built up inside. Unfortunately, the fan still runs at full speed. 

My bios seems to not have any controls for fan speed / temp. the bios is phoenix award and up-to-date (last upgrade was from 2003). the computer is an old beast from 2003. P4 2.4 socket 478 with stock heatsink/fan. unknown motherboard (msi?). medion desktop. nothing special. 

I suppose my next plan is to replace the heatsink/fan or see if lm-sensors/pwmconfig is compatible with my setup to see if I can just lower the speed. I am not sure if the motherboards is replaceable since the case is rather compact -- I have not investigated that option, however. the cables/connector to the fan seems fine -- no fraying or broken/bent connectors. 

other than that, I guess there's no harm in having the fan run at full speed other than the annoyance. 

thanks

---

### Post by Skripka on 2009-09-08
> **bionnaki said:**
> the CPU fan on my desktop never turns off -- it just runs at full speed from the moment the computer is switched on and never varies like it used to in regards to processing tasks. I know it's the CPU fan and not the power supply fan because I unplugged the CPU fan from the motherboard and that particular sound was gone.

obviously, I cannot keep the fan unplugged...but the sound is driving me nuts. my computer has been running like this for 3 months now, but now that I've moved the computer into my bedroom has it been really noticed. I'd rather find a solution other than move the computer into another room. 

what could be the cause of this problem? I figure it's either a problem with the fan itself, the PSU needs to be replaced, or the motherboard is messed up. the bios is up-to-date (I do not have any fan options in the bios, as far as I can tell). 

any input would be greatly appreciated.

Firstly, Do NOT (ever) run your computer without a HSF running on your CPU.  It is an easy way to VERY quickly damage your machine.

Secondly-are you using a stock heatsink?  If so this is not surprising.  They tend to be loud, and inefficient at removing heat.

3rdly, like the stock HSF itself, the stock thermal compound on stock HSFs just plain sucks.  Replace it with Artic Silver 5.

If after doing #3, then replace the HSF--and use AS5 thermal compound (NOT what comes with the new aftermarket HSF).

---

### Post by bionnaki on 2009-09-08
thanks for the tips. that will be my project this week.

---

### Post by bionnaki on 2009-09-09
well, I thought I'd play around with lm-sensors/pwmconfig. I followed a guide and installed/configured correctly.

and my fan now has the ability to slow down/speed up according to temperature! The normal, static fan rate is very acceptable and back to the way it used to be. I guess the fan was not broken after all -- not sure why the fan speed variation would not work before, though.

temperature is a cool 27 C and my computer is near silent.

---

### Post by MikeTheC on 2009-09-09
[font=arial][size=4]WHAT? CAN YOU SPEAK UP? I CAN'T HEAR YOU! YOUR COMPUTER IS TOO LOUD![/size][/font]

[font=courier]</sarcasm>[/font]

Sorry, I couldn't resist. This thread was just calling out to me, begging me to make a witty retort. Best wishes in solving your fan noise problems.

---

### Post by bionnaki on 2009-09-09
already solved my man.. \\:D/

---

