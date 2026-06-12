---
title: "pan p7 -- fan keeps cycling on, off, on, off, etc."
date: 2012-02-13
forum: System76 Support
---

### Post by Gurtz on 2012-02-13
Hi,

I have a new problem with my pan p7 (at least I think that's what it is; bought it from System 76 in December '09). Just in the last few days I've noticed that the fan is constantly turning on (for about 3 seconds), off (for about 1), on (for 3), off (for 1), etc. [This is during times of low usage, with very little process activity. The fan shouldn't be needed at all.] It's extremely annoying to listen to, and I can't imagine it's good for the machine, either. I'm running Ubuntu 10.04 LTS.

Can anyone give any thoughts on how to resolve this issue?

Thanks so much,
Greg

---

### Post by Andrew_P on 2012-02-13
Try running GNOME System Monitor (System --> Administration --> System Monitor) to see if any application is putting a heavy load on the CPU while the fan is exhibiting this behavior.

As I sit here, compiz is using 1%-3%, gnome-system-monitor is using 9% and seamonkey-bin is using 20% to 25%.  There are a couple of dozen other processes that all show 0% CPU.

If there aren't any processes that are heavily loading your CPU, it could indicate a failure of the mechanical interface between the CPU package and its heat sink.  I recall recently watching a [_[COLOR="Blue"]how-to video on YouTube[/COLOR]_]("http://www.youtube.com/watch?v=bnkQNmKauEc") showing how to repair a blank screen problem in an HP DV-series laptop computer.  Apparently, to save money, HP had taken some design shortcuts and had been omitting thermal grease between the video IC package and the heat sink.  Under high load the package could overheat to the point that the Ball Grid Array (BGA) solder joints under the package fail.  Although an expert technician can remove the BGA from the motherboard, clean it up and reflow it onto the board, if one were to ship it in to HP for service, they'd probably deem it uneconomical to repair.

Your System76 Pangolin Performance 7 laptop computer is obviously still working, but may be suffering from a similar malady to that experienced by many HP laptop owners.  I suspect *most* of the BGA solder joints are still intact, but a few may already have separated from the motherboard, i.e., those connecting to the power buses and/or power ground plane.  The power planes are also used for heat removal, in addition to a heat sink placed on top of the package.  Normally, it takes a while for the CPU die to heat up and raise the temperature of the heat sink mass; if the heat sink mass becomes disconnected, the temperature rise will be very rapid, causing the on-die temperature sensor to turn the fan on and/or throttle back the system clock; the temperature of die then drops rapidly, the fan is commanded to turn off, the CPU cranks up again, and the cycle repeats.

My recommendation is to run the machine with adequate ventilation; never set it on a surface where the air ports get blocked, e.g., sitting on your lap or on a soft fabric surface.  If the rapid fan cycling persists, consider having the machine disassembled to gain access to the CPU heat sink and get some thermal grease applied between the CPU package top and the heat sink.  If that doesn't cure it, the last resort would be to reflow the package, replace the CPU package, or rescue your data and toss the machine. :(

***From your description, the machine may be just hours away from quitting completely.  I'd begin backing up the data without further delay.***

---

### Post by isantop on 2012-02-13
We've never had an issue like that happen on any of our laptops. All of our systems use thermal compound between both the CPU and GPU (where applicable) and the heat sink. My guess is that there is dust of some other debris plugging the fan up. Go ahead and remove the battery, then pull the large main panel off of the bottom of the computer. Be careful to gently unplug the fan connector; the fan plugs into the motherboard, but is attached to the panel itself. 

With that free, use a can of compressed air to clear out any dust clogging the heat sink as well as the fan. Use short, gentle bursts to avoid damaging the motherboard or other components.

When you're finished, reassemble the computer (don't forget to plug the fan in), then try it and see if the problem comes back.

---

### Post by Andrew_P on 2012-02-13
> **isantop said:**
> With that free, use a can of compressed air to clear out any dust clogging the heat sink as well as the fan. Use short, gentle bursts to avoid damaging the motherboard or other components.

It would be great if that's all it takes to fix it.

I'm in the habit of taking my computers outside about once a year and using a rubber-tip blowgun and hose connected to shop compressor at about 30 psi to clean all the dust out.  I've been doing that since the mid-1980s and I've never had issues with overheating components.  If the computer is used in a humid environment the dust can get stick on the surfaces.  This can be remedied by gently brushing with a natural bristle brush and then blowing it clean.  I use an inexpensive 1-1/2 inch paint brush.  One shouldn't use synthetic bristles, as they can generate static and destroy CMOS parts.  Of course, this presupposes that one has full access to the innards of the machine.  Blowing shop air or "canned air" through openings is the next-best thing.  Where possible, fan blades should be thoroughly cleaned to maximize their efficiency.

---

### Post by Gurtz on 2012-02-13
Thanks to both of you for the very helpful replies!

Fortunately, the cycling on and off of the fan seems to have stopped, but I think it is still running more than necessary. I'm definitely going to try to clean it (and bought some compressed air today for that purpose). I don't have time at the moment -- will probably wait till the weekend -- but I'm hopeful that a good cleaning will help everything run more efficiently and predictably.

BTW, none of the vents are obstructed, and the laptop is sitting on a raised platform with air holes underneath. [I use an external keyboard, so I don't typically need to reach the laptop keyboard. And the raised platform increases my available desk space.]

Thanks again. I really appreciate you taking the time to respond.

All the best,
Greg

---

### Post by isantop on 2012-02-14
> **Andrew_P said:**
> It would be great if that's all it takes to fix it.

I'm in the habit of taking my computers outside about once a year and using a rubber-tip blowgun and hose connected to shop compressor at about 30 psi to clean all the dust out.  I've been doing that since the mid-1980s and I've never had issues with overheating components.  If the computer is used in a humid environment the dust can get stick on the surfaces.  This can be remedied by gently brushing with a natural bristle brush and then blowing it clean.  I use an inexpensive 1-1/2 inch paint brush.  One shouldn't use synthetic bristles, as they can generate static and destroy CMOS parts.  Of course, this presupposes that one has full access to the innards of the machine.  Blowing shop air or "canned air" through openings is the next-best thing.  Where possible, fan blades should be thoroughly cleaned to maximize their efficiency.

You'll want to take care with using an Air Compressor. Air Compressors take normal air and compress all of it's parts; including the water vapor. When compressed, this vapor can condense into liquid water, and you might end up blasting your computer with water! If you're going to use a compressor, be sure to use very short bursts, and it would be a good idea to remove the battery as well, to ensure the computer doesn't short.

---

### Post by jschall1 on 2012-02-15
> **isantop said:**
> You'll want to take care with using an Air Compressor. Air Compressors take normal air and compress all of it's parts; including the water vapor. When compressed, this vapor can condense into liquid water, and you might end up blasting your computer with water! If you're going to use a compressor, be sure to use very short bursts, and it would be a good idea to remove the battery as well, to ensure the computer doesn't short.

I work in a computer store that uses an (unfiltered) air compressor to blow out every single machine. Never an issue, except that the manager once managed to blast the fins off of a laptop fan. It was some cheapo acer or something, of course. Never had a problem blowing out a desktop, though.

However, air compressors can and do spit out water sometimes. I don't know why that one doesn't, probably because it is regularly used for fairly long periods of time.

---

### Post by Andrew_P on 2012-02-15
> **isantop said:**
> You'll want to take care with using an Air Compressor. Air Compressors take normal air and compress all of it's parts; including the water vapor. When compressed, this vapor can condense into liquid water, and you might end up blasting your computer with water!

Good point, but it would only a problem if done under high humidity conditions, especially if the hardware were cold.  Since the computer is usually very dusty when I do this, I always do it outdoors, and since I don't like to be outdoors in cold weather, I do it on a warm, sunny day with the hardware at ambient temperature.
  
> **jschall1 said:**
> However, air compressors can and do spit out water sometimes. I don't know why that one doesn't, probably because it is regularly used for fairly long periods of time.

I also take care to drain condensate from the compressor tank from time to time, so air coming out of the hose is as dry as it can be.  Compressed air tanks are usually fitted with a small drain c o c k at the bottom for this very purpose. ;)

**Note:** They're a bit overzealous with censorship on this forum.  That's why I had to space the letters of that piece of hardware out in a silly fashion.

---

### Post by Gurtz on 2012-02-17
Got a follow up:

I used compressed air to clean out the dust from inside, but there wasn't much at all. Unfortunately, it has not made any noticeable difference. The fan is running almost continuously, and at what seems to be a fairly high average rate.

I installed some sensors under Ubuntu 10.4 (lib-sensors, sensor-applet), and it is showing that the CPU temperature is 47 degrees C, and the GPU temperature is 93 degrees C. The latter is high, isn't it? [The CPUs are running at about 25% average utilization.]

I've got a NVIDIA GeForce 105M. I don't play any games, and can't imagine I'm stressing the GPU very much. Just web browsing, email, etc. on a dual screen setup.

Thoughts??

Thanks,
Greg

P.S. Found out it's a pan p6, not p7.

---

### Post by Gurtz on 2012-02-18
Some more details:

I've found that running a dual screen setup is part of the problem (or, at least, it is making the problem worse). NVIDIA uses a "PowerMizer" library/tool to automatically adjust the GPU clock speed, based on system load. I read somewhere that -- whether it needs it or not -- "PowerMizer" will always use the highest power setting when on a dual screen setup. That means that, when using dual screens, the graphics clock runs continuously at 640MHz (the highest setting). When running with just one screen (LCD or external, doesn't matter), the clock speed fluctuates, and -- as I type this -- currently sits at 169MHz (the lowest setting). This likely explains why the GPU temperature was always so high. 

That said, the GPU temperature still seems high to me. It currently sits at 62 degrees, which is the lowest I have seen since having this problem. Even with mild use (on a single screen) it sometimes goes up to 80 degrees. Why?

I opened the PC again, and checked both of the heat sinks (CPU and GPU), and they both seem to be fitted correctly, with no obvious issues. [And again, no dust.]

Any thoughts on what can be done to remedy this problem? I'm currently nervous to go back to dual screen for fear of burning out my system. Yet I really LIKE dual screen :-(

Any help would be appreciated.

Thanks,
Greg

---

### Post by isantop on 2012-02-20
> **Gurtz said:**
> Some more details:

I've found that running a dual screen setup is part of the problem (or, at least, it is making the problem worse). NVIDIA uses a "PowerMizer" library/tool to automatically adjust the GPU clock speed, based on system load. I read somewhere that -- whether it needs it or not -- "PowerMizer" will always use the highest power setting when on a dual screen setup. That means that, when using dual screens, the graphics clock runs continuously at 640MHz (the highest setting). When running with just one screen (LCD or external, doesn't matter), the clock speed fluctuates, and -- as I type this -- currently sits at 169MHz (the lowest setting). This likely explains why the GPU temperature was always so high. 

That said, the GPU temperature still seems high to me. It currently sits at 62 degrees, which is the lowest I have seen since having this problem. Even with mild use (on a single screen) it sometimes goes up to 80 degrees. Why?

I opened the PC again, and checked both of the heat sinks (CPU and GPU), and they both seem to be fitted correctly, with no obvious issues. [And again, no dust.]

Any thoughts on what can be done to remedy this problem? I'm currently nervous to go back to dual screen for fear of burning out my system. Yet I really LIKE dual screen :-(

Any help would be appreciated.

Thanks,
Greg

You're unlikely to cause damage to the system by using the external monitor. The laptop's cooling system was designed to take the brunt for the GPU running full-on. And, in the event it *does* get too hot, it will shut down automatically, so you won't *damage* the GPU.

Also, are you using the Proprietary Nvidia Driver? The proprietary graphics drivers often have better power management support than other drivers, and often run cooler.

---

