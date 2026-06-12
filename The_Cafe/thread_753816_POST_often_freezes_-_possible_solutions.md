---
title: "POST often freezes - possible solutions?"
date: 2008-04-13
forum: The Cafe
---

### Post by 3rdalbum on 2008-04-13
Hi all,

I just built a computer for a friend of mine, using the Asus M2A-VM-HDMI motherboard. Running Ubuntu, of course.

But quite frequently, it will freeze up during the BIOS graphic screen. If you press the reset switch, it still won't work. If you try to go into the setup screen, it will still freeze. If I press the key to bring up the BIOS text, it shows that all the memory has been checked, but doesn't get any further than that.

If I open up the case at all, put the case back on and boot up, the computer will start up and be rock-solid stable. If I reboot the computer, even if I shut down and start up again, the computer will boot.

I have no idea what could be going wrong. When the computer does start up, everything is normal - temperature readings are normal, the system doesn't crash, all peripherals work.

Any suggestions? The PSU is a 350w CoolerMaster that came in the case, the RAM is 1 gig of Kingston (yet to run a full Memtest) shared with the integrated ATI graphics, the DVD burner is IDE and the hard drive is SATA. The processor is an Athlon X2 4200 with the standard heatsink/fan combo. I think the BIOS is a Pheonix.

If nobody here has any ideas, I'll have to swallow my pride and take it to the place I bought the parts from. :-(

---

### Post by PmDematagoda on 2008-04-13
Did you check the RAM? Faulty RAM can cause the problems you are talking about.

---

### Post by Tundro Walker on 2008-04-13
I guess I don't quite follow what's going on.

* You start it up.
* It boots to POST then freezes up
* But if you open the case and reset or something, then it boots up?


Usually the comp will let out some beeps to signal what's going on.  You should be able to look up the motherboard specs online to see what the BIOS / POST beep signals mean.  EG: normally one long, continuous beep means the graphics card is missing (if there isn't one built-in).  Three beeps could mean a missing keyboard.  And so forth.  The beep signals can be different between BIOS'.

Now, if you take the case off after it freezes, is it warm inside?  It could be over-heating, and it won't reset / reboot until the cpu cools down.  Did you apply something like Arctic Silver thermal compound between the cpu & the heat sink when putting it on?  And, did you set up some proper air flow?  IE: lower fan sucks in on the case, circulates upwards towards the cpu, gfx card & ram, then cpu fan vents off the cpu, and eventually the hot air circulates towards the upper / back of the comp to get vented off by the PSU and usually a secondary case fan?

If your cpu isn't hot, could it be that your gfx card is burning up due to poor circulation?  Could there be a short occurring?  Maybe some wiring is just scrunched around causing some kind of grounding on the case when it shouldn't.  Also, make sure all the cards & ram are pushed in firmly into the mobo.  Don't break it, but I have had situations where it seemed like the ram was all in, but it wasn't and thus wasn't showing up in mem check.  Had a network card, too that I had to cram in pretty good for it to finally get acknowledged.  Just be careful you don't break something.

Another thing to check is maybe a 350w power supply isn't enough to handle everything you've got going.  Some PSU's have a power setting switch on back.  Crank it up to the higher setting and see if that resolves it.  Or, try swapping in a 400w PSU, or research online to see what the ideal wattage would be.

There's just so many things that could be wrong, it's hard to tell from the vague description you gave.  But, usually if the BIOS is freezing up after POST, it's either a power or overheat issue.

---

### Post by 3rdalbum on 2008-04-13
I know it's an oversight, but no I haven't done a full Memtest yet.

The motherboard just beeps the once - the usual short beep to tell you that it's powering up. There are no error messages on the screen, and no extra beeps.

I don't think cooling is the issue. The fans are running, and when the computer does start up (or get to the BIOS setup screen) the temperatures reported by the CPU are well within tolerance (30 degrees celcius, basically). I haven't noticed any particular warmth, and once I ran it in its frozen state for a few minutes before turning it off and opening the case.

I always close the case again before turning the computer back on.

I was suspecting power supply issues, but from what I've read I should still have some headroom with my particular system. If all else fails I'll bring it back home and hook it up to my main computer's 500 watt PSU.

I'll also try taking out and reinstalling the RAM. It's an integrated graphics chipset, so thankfully I don't have that worry :-)

Thanks for the suggestions, I'll try them tomorrow night. I was stumped because I couldn't think of a reason why it would sometimes not work; and when it does work, it runs like a dream.

---

### Post by diablo75 on 2008-04-13
I think the easiest way for you to troubleshoot this is to remove all the expansion cards you have in the system (with exception to the video card) as well as all but one stick of ram.  See if POST locks up with a bare minimum hardware configuration.  If you encounter no errors or lockups, shut down, add another stick of ram, test it again.  Keep this going till you're out of RAM.  Then add a PCI card one at a time, shutting down between each upgrade.

Hopefully, if there is a faulty hardware device (be it an expansion card, or a stick of memory) doing this will help you narrow down the cause.  Good luck!

---

### Post by smoker on 2008-04-13
just a suggestion, do you have a floppy drive, or usb drive connected during boot? if you don't have a floppy, make sure this isn't an option in the boot sequence, else the bios may halt looking for a non-existent device, also, if capable of usb boot and you have a usb drive attached, make sure that usb boot option is disabled else the bios may be looking for a boot sector there. best is to have the hard drive as the first boot device.

best of luck

---

### Post by Trollslayer on 2008-04-13
This usually a connector not in place properly even though it may look like it its.
**Making sure you are earthed using a wriststrap** remove all the addin cards, reset the DIMMs and make sure the power supply plug is in properly.
Also use the jumper on the motherboard to clear the CMOS memory.

---

### Post by rustutzman on 2008-04-13
Does it have a chassis intrusion switch? If it does than disconnect it from the motherboard. Odd that doing nothing more than opening and reseating the case would allow it to start.  Another possible problem might be a wire getting pinched in the sides of the case. Look very carefully for this as it's easy to miss.

The other posters have given good advice in removing everything except what's need to boot.

Russ

edit: Also unplug all USB devices and try it.

---

### Post by 3rdalbum on 2008-04-16
An update:

I did a full pass of memtest - the RAM checked out okay.

Just now, I ran Frets On Fire then quickly shut off the computer and opened the case. I put my fingers on the big CPU heatsink and it was cooler than the other heatsinks on the motherboard. Is this normal, or does it indicate that the heatsink isn't in proper contact with the CPU? The CPU tends to run at 40 degrees celcius under load anyway, according to lm-sensors.

@diablo75: There's only one stick of RAM, and I observed the problem occurring whether there was an HDMI output card plugged in, or a wireless card. But then, the system sometimes runs with these things plugged in. I only briefly had the machine without either card. I shall try it without either card as well.

@smoker: No floppy drive, no USB drive, and I've already disabled the floppy boot option. But thanks for the suggestion.

@Trollslayer: Thanks for the suggestion, I found that I'd put the memory into the second yellow slot. Can't remember why. It's now in the first yellow slot and seems to be working, but it's only been a couple of hours.

@rustutzman: No chassis intrusion feature on the chassis, so that made things fairly simple.

I also ran the BIOS update for that motherboard. It didn't seem to change anything.


I'm wondering whether it's possible that RAM can be unstable straight after turning on the computer. My friend also complained that she had turned on the computer and had the chassis fan running, but heard no beeps and got nothing come up on the screen. I disabled "quick boot" and so far it's been running alright. I'd wondered if the BIOS was putting data into memory before the memory was actually stable. Maybe that's just an uninformed idea.

I also checked all the connections; reseated the RAM and reinstalled the wireless card. It doesn't naturally hang from the slot correctly to just be screwed in, so this time I haven't screwed it in.

---

