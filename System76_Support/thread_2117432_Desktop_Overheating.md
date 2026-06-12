---
title: "Desktop Overheating"
date: 2013-02-18
forum: System76 Support
---

### Post by Teasdale on 2013-02-18
This is a follow-up to this thread:
[http://ubuntuforums.org/showthread.php?t=2082434](http://ubuntuforums.org/showthread.php?t=2082434)

I have a Ratel Ultra desktop which is a little over a year old (out of warranty). I installed a new version of Ubuntu as suggested, the system continued to shut down, I sent the computer in to System76, and they said the hardware looked fine and they were able to start it up with no problem, so they sent it back.

So I set it back up and plugged it in yesterday and it started up, but it's still randomly shutting down. This time, I got an error message on one occasion that said "thermal event (overheating)", and after googling, it seems that random shutting down is a typical symptom of an overheating problem, so I think that's probably what's going on. I opened the tower, vaccuumed the CPU fan, but other than that, I don't know what I should be looking at (and I can't spend another $90 to send the computer off again without it coming back working).

I'm not sure where to post for help. System76 has already looked at the computer, so this issue is not necessarily relevant here, although the hardware was put in by System76, so maybe it *is* relevant here, as knowledge of the hardware specifics could make it easier to pin down an issue? Would it be more effective to post in the Hardware area of the Ubuntu forum?

---

### Post by isantop on 2013-02-18
> **Teasdale said:**
> This is a follow-up to this thread:
[http://ubuntuforums.org/showthread.php?t=2082434](http://ubuntuforums.org/showthread.php?t=2082434)

I have a Ratel Ultra desktop which is a little over a year old (out of warranty). I installed a new version of Ubuntu as suggested, the system continued to shut down, I sent the computer in to System76, and they said the hardware looked fine and they were able to start it up with no problem, so they sent it back.

So I set it back up and plugged it in yesterday and it started up, but it's still randomly shutting down. This time, I got an error message on one occasion that said "thermal event (overheating)", and after googling, it seems that random shutting down is a typical symptom of an overheating problem, so I think that's probably what's going on. I opened the tower, vaccuumed the CPU fan, but other than that, I don't know what I should be looking at (and I can't spend another $90 to send the computer off again without it coming back working).

I'm not sure where to post for help. System76 has already looked at the computer, so this issue is not necessarily relevant here, although the hardware was put in by System76, so maybe it *is* relevant here, as knowledge of the hardware specifics could make it easier to pin down an issue? Would it be more effective to post in the Hardware area of the Ubuntu forum?

Try plugging the computer into an outlet on a different circuit. It may be that the power is fluctuating and causing this.

---

### Post by Teasdale on 2013-02-18
OK. I do have a battery back-up that's supposed to even out power. In fact, when the problem started, I purchased a brand new battery back-up replacement, thinking it was a power problem. I can try plugging it into a different outlet, though.

---

### Post by macpj on 2013-02-19
Make sure all vents and fan's are clear of dust. Especially the power supply fan. When vents get clogged that can skyrocket the temperature of a PC. Keep a supply of canned air on hand. I blow out my machines every 1-2 weeks, especially in the winter time when the heat is constantly on. We have a gas forced air heat system in our house and that dries out the air and creates more dust than usual.Also, make sure there is good air flow around the PC case. If you have it shut up in a cabinet while it's running, that will kick up the temp big time. Hope this helps...

---

### Post by tgalati4 on 2013-02-19
I would remove the heat sink from the CPU and check the condition of the heat paste.  Too much, or poorly applied can cause CPU overheating and shutdown.  Check the thermal warnings in the BIOS, set them slightly lower so that you get a warning sound instead of an abrupt shutdown.

Put a better quality (silver, or ceramic) heat paste and follow the web guides for how to apply it.  Not too much, and evenly applied to a clean surface.

Once that is done, and you still get shutdowns, then I would suspect the power supply.  Try replacing it with a new one or one from a known working computer.

If you still get shutdowns with a new/known-working power supply, then I would suspect a motherboard issue.

Try removing everything not essential.  One stick of RAM, and boot a Live DVD and run that for a while and if it shuts down again, then I would definitely suspect the motherboard.  It's unfortunate for such a new machine, but the tight tolerances of todays high-performance machines means less robustness.

It's possible that the UPS has gone bad.  The relays or circuitry can and do fail.  Run the above tests without the UPS to see if it crashes without the UPS.

---

### Post by Teasdale on 2013-03-07
> **tgalati4 said:**
> I would remove the heat sink from the CPU and check the condition of the heat paste.  Too much, or poorly applied can cause CPU overheating and shutdown.  Check the thermal warnings in the BIOS, set them slightly lower so that you get a warning sound instead of an abrupt shutdown.

Put a better quality (silver, or ceramic) heat paste and follow the web guides for how to apply it.  Not too much, and evenly applied to a clean surface.

Once that is done, and you still get shutdowns, then I would suspect the power supply.  Try replacing it with a new one or one from a known working computer.


Thanks, I'll try those as well as making sure the vents and fans are clean.

The computer was packed up and sent to System76; they looked at it and they said there is no hardware issue.

---

### Post by Teasdale on 2013-04-08
This was finally resolved and SOLVED a couple days ago. I had a friend take a look at it with me; he discovered that the cable going from the hard drive to the motherboard was touching the fan and apparently sometimes that was enough for the fan to refuse to spin. We twist-tied the cable out of the way, and the computer has been fine since then. Because the tower for the Ratel Ultra is so small, there's not a lot of room for the power box and everything, cords and cables have a harder time staying out of the way.

I can't believe this computer has been out of commission for almost six months (I've been trying to figure this out since October) for something so minor. But I am glad to have my computer back again! :)

---

