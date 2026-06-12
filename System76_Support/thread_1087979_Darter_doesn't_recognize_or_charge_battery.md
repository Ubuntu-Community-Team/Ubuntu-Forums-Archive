---
title: "Darter doesn't recognize or charge battery"
date: 2009-03-05
forum: System76 Support
---

### Post by dnarnold on 2009-03-05
I left my Darter 1 (daru1, the white one) on battery power until
the battery drained.  When I plugged the AC power back in again, the laptop
didn't recognize that there was a battery installed and won't charge it.
The battery charging LED (2nd LED from left) doesn't light, the various
power utility programs report that no battery is present, and the battery
doesn't charge whether I leave it in while the laptop is powered on or
plugged in but powered off.

Help!  Any ideas?  Thanks -- Doug

---

### Post by thomasaaron on 2009-03-05
Try re-setting the CMOS.

Remove your ac adapter and battery. Let everything cool down to room temperature. 

There's a little hole beneath the leading edge of your DarU1 -- right under your left palm. It is a hole with two arrows pointing towards it. Stick a paper-clip in there and depress the CMOS switch. Hold it for about 15 seconds.

The replace your ac adapter and battery.

Did that fix the problem?

---

### Post by dnarnold on 2009-03-06
Thanks for the quick response.  I followed your instructions (removed ac
adapter and battery, let cool, inserted paper clip to depress emergency
shutoff switch hole on bottom of laptop directly beneath the left touchpad
button, held it depressed for 15 seconds, and then reinstalled the ac
adapter and battery), but it didn't work.  When the machine rebooted I
ran "acpitool -B" and still got "Battery #1     : slot empty".

Your suggestion of the CMOS brings to mind a second sympton which could
be related.  Some time ago (months) I started having a problem that
the system clock would sometimes be hours off after a reboot.  I meant
to check into it, but in the meantime wrote a script to reset the time
with ntpdate when I log in, and I forgot about it.  Might I have a bad
CMOS or CMOS battery?

 -- Doug

---

### Post by thomasaaron on 2009-03-06
Yeah, that's a definite possibility (i.e. the battery). It is not really changeable at the user level, though; it requires removing the MB, I believe.

Shoot me an email at support(at)system76(dot)com, and we can look at repair options (not sure of your warranty status).

---

### Post by thomasaaron on 2009-03-06
Hi, Doug.

I'm getting your email, but when I try to reply, it bounces back. So I doubt you are receiving them.

If you can email me from a different email address, that would be helpful. In the meantime, here is what I emailed you...

Hi, Doug.

The CMOS battery seems like the most likely cause to me. The flashing LEDs are a kernel panic. They *could* be caused by a power fluctuation, I suppose. But it is more likely that they are caused by some piece of software that you are running, as I've not heard of any other kernel panics on the DarU1.

If it happens again, here is what you can do...
1. Immediately shutdown and re-start your computer.
2. After re-starting, note the time on your system clock.
3. Go to System > Administration > System76 Driver > Support > Create.
4. Send me the logs.tar file created in your home directory.

I'll have a look and see if I can figure out what is going on.

Best,
Tom

---

