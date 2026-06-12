---
title: "power glitch in AC leads to locked off AC to DC power in laptop power box"
date: 2024-02-16
forum: System76 Support
---

### Post by Skaperen on 2024-02-16
when there are power glitches or short flickering, the power box that converts AC to 19v DC for my Kudu Pro purchased in early 2014 will shut down and "lock off" and not send any more 19v DC to the laptop.  slow-cycling the AC power resets this and the laptop will get power, again.

IMHO, a power supply should not be intentionally designed to do this and, instead, should monitor for stable AC in the acceptable voltage range for a period of N seconds a resume power conversion when that happens.  i would set that to be about 8 seconds on battery-less devices (devices with battery should be able to ride though glitches, flickers, and outages).

my question is if this issue still exists in 2024 for any System76 laptop sold today.  i am joining the market for a new laptop top to run Xubuntu (i will install) and want to know if this issue is now gone.  i don't want to transport one of my heavy dual-conversion UPSes around to deal with such power issues.

does someone at System76 know what inside these power boxes is holding the power off?  is it something specific in the circuit or just a side effect of how it was designed?  a tiny processor with unknown code?

---

### Post by him610 on 2024-02-18
>  the power box that converts AC to 19v DC
Are you referring to the AC adapter that came with your System76 device? Sounds like your AC adapter may be on its last legs. You may want to consider replacing it. They are relatively inexpensive.

We have System76 Pangolin from about early 2013. Never had any issues with the AC power adapter; however, we do not have any "power glitches or short flickering" to speak of here in south-central Pennsylvania. We did get a lightning strike once; it came right down the coax cable. It fried the cable modem, a router, a motherboard, and a laser printer. Insurance covered about $900 for the damaged items; it was considered an "Act of God." Ever since then, I have my basement devices connected to a UPS device . 

Since you seem to live in an area that has inconsistent AC power, you might want to consider an *ac power filter power conditioner*, or a *ups battery backup & surge protector*. Either one will protect your expensive electronic equipment.

---

### Post by Skaperen on 2024-02-18
the AC power issues are not surges.  they are power "blinks".  they would get through most UPSes because it's such a brief outage.  what i need is the "dual conversion" type that are always converting DC to AC with the battery in parallel with the DC it converts from the AC with some big capacitors on the DC.

i used to have one of those (don't remember what happened to it) many years ago.  it was a 240 volt unit (needed a special dedicated 240 volt 20 amp circuit to power it).  240/208 in, 240/208/120 out, 3000 VA capacity.  it was about the size of 3 PC towers.  it had 9 outlets on the back (one was for 240 volts out).

---

### Post by Skaperen on 2024-04-18
blinks of this type tend to be causes by a power company distribution fault on a branch somewhere else.  something, such as a falling tree/branch or a drunk driver causing a brief phase-to-phase or phase-to-neutral "short circuit" quick enough to avoid tripping various protection means.  perhaps power does not even go out, but just dips down to a low voltage and backup.  cheap surge detection might see this as a surge and have this lockout as protection, figuring the laptop battery has hours of charge on it.  still, IMHO, it should have a "power has been clean and stable for N seconds" come-back-on circuit.  this is easy enough if it has the ability to check power when comes on:  just do a clean cut of the AC after N seconds and back on after N+ seconds.  then your battery won't run down while you are away.

---

