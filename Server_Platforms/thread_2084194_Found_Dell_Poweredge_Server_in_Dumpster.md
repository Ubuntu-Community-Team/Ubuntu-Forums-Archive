---
title: "Found Dell Poweredge Server in Dumpster"
date: 2012-11-14
forum: Server Platforms
---

### Post by misterfixit on 2012-11-14
I dumpster dive a lot.  This morning I found a Dell Poweredge 840 Server box complete with 4 attached 160GB hard drives in the hot-swap RAID compartment.  I went to the office where I figured it had come from and they told me "Oh the Dell guy said it is toast and they are bringing a new server".  Ah-Ha.  Iasked about the hard drives and got a blank look.  OK, I got it home and plugged it in with a 15" flat monitor (another dumpster item) and keyboard and mouse.  I hear the POST begin then followed by comtinuous beeping.  According to Dell this means the CPU is fried.  I pulled it apart, vacuumed it out (had never been done, evidently) and tried to POST just the MoBo without accessories, SATA, RAID, etc. with only the existing 2GB of RAM and the CPU.  Still beeps.  OK, out with the RAM, still beeps, OK out with the CPU .. POST now is quiet but nothing on the VGA -- I am thinking monitor won't display without a CPU?  Anyway, I pulled each of the HD's and looked at them.  They had been quick-formatted but loads of stuff still on them.  I used my existing Ubuntu system to format then to run the HD test which is supposed to overwrite with bunches of zeros adn ones.  Not interested in someone's personnel records.  Now for the challenge.  I am thinking that I should start by replacing the Xeon Dual Core 3040 1.86 CPU.  What say you all?  It is a Quad Core aand uses the old LGA775 socket.  Since this is a freeby, I'll expect to hear at least one answer here other than "can't play Doom-3 on it, use it for your .50 caliber machine gun target.  Thanks in Advance,

---

### Post by lykwydchykyn on 2012-11-14
Wow, this was literally in the dumpster?

If you have a compatible CPU readily available, I'd give it a try, but I'd be reticent to spend money on it, since it could be something else in the system gone wrong.

If a CPU is fried, you have to ask yourself *why* the CPU is fried -- defective motherboard?  Defective power supply?  Some other component spiking the electrical system?

Of course it could have just been a defective CPU or a lightning strike or something, but unless you know that for sure, you stand the chance of ruining a good CPU.

---

### Post by misterfixit on 2012-11-14
I've measure the voltage from the power supply and it matches specs.  No evidence of burning, etc.  My suspicion is that the CPU is fried due to high temperatures.  It has a 5" tall radiator fin assembly on top of the CPU and that was completely clogged with dust all the way down to the CPU shield which sits like a cover over the CPU in the socket.  Everything else was full of dust.  Fans power up OK; USB ports are showing 3.3 volts; LED's reboot button and other obvious stuff works.  I pulled the MoBo battery and replaced that and pulled the two jumpers from the "Password On Always" (part of the POST).  Still no vga disply which SHOULD be there even with no CPU and nothing else plugged into the MoBo.  Not going to get into DELL's wierd way of doing their thing, but MoBo has no obvious test points.  My next step is to take a working MoBo and put it inbut the dead-bug and hanging wire method and see what the periphals look like when plugged into a working MoBo.  Then will try to find that matching CPU someplace .. ebay has 'em for $30 or so.  I get this box working and it will run my Ham Radio Satellite tracking and automatic transceiver system for using the AMSATs, but only if I can do this for under $50 or so.  What think you?

---

### Post by Moose on 2012-11-14
All that in a dumpster? Nice find "Diver Fxit" :D

---

### Post by drmrgd on 2012-11-14
Very cool!  As long as the Mobo is OK, sounds like you might have a nice little toy to play with.  Good luck with it!

---

### Post by misterfixit on 2012-11-14
> **AnarchyTech said:**
> All that in a dumpster? Nice find "Diver Fxit" :D

You all should dumpseter dive more arond large office buildings.  I have several friends of mine who are security officers (rent-a-cops) and when there is a big dump they text me.  I've rehabbed about 15 workstations in the past 2 years and have donated them to either our local Boy Scout troupe's Ham Radio Station, or to local Ham operators who are living on a fixed income (old farts like me only without the Apple Stock bought at $25 during the IPO).  Virtually ANY PC can be rehabbed if you take a methodological path to the refurbishment.  I get rid of the 5 and 3 inch floppy drives, toss the CD ROM only devices and do a complete cleaning of the guts.  I have plenty of spare parts around to fix a lot of stuff.  I do draw the line at 286 machines and the early 386 boxes except when someone asks me for one that is just for email.  I did come across a whole load of old IBM PS machines a few years back and rehabbed them; for you old timers the old IBM's were built like tanks and everything was non-standard.  TYpical.  But they will run Linux and one of the tiny sized graphic displays.  We waste too much stuff and especially businesses which have only a couple of years or so and they replace everything based upon the concept of tax write-offs and capitalization of assets.  Their loss is our gain.  Just remember, and I absolutely emphasize this, if you find ANYTHING on the hard drives, delete it immediately no matter how temped you are for just one more copy of the Debbie Does Dallas outtakes video.

---

