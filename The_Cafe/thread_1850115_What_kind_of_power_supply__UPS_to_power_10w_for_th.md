---
title: "What kind of power supply / UPS to power 10w for three days"
date: 2011-09-25
forum: The Cafe
---

### Post by needhelpplease on 2011-09-25
I'm not sure where to post this so I'm posting it here...

Here's the situation:

We have a warehouse that only gets power from 9-5 M-F.  It would be nice if we had 24/7 power but can't change it; we don't have control over the operations of it.

I need to install one webcam with a wifi router (WRT54G and a regular Linksys camera).  Total draw of the WRT54G is about 3W and the camera is probably a few more watts, so let's call it 10W.

I know there are UPSes out there but none of the UPS calculators are for this kind of usage, of powering a very small load (10W, equal to about 1/10 of a desktop PC+monitor) for a long time (up to 72 hours).

Any suggestions on this?  What size UPS should I get, or will a UPS be the right thing to use?  I wonder if one of the regular desktop UPS units that go for about $150 would do the job?

Thanks

---

### Post by tgalati4 on 2011-09-26
Buy the cheap one and test it with a 15 watt light bulb.  Use a stop watch or watch the clock.  When the light goes out, then you have exhausted the battery.  Let's say you get 10 hours out of it.  Pull the battery and look at it's capacity.  Perhaps a 12VDC, 12 Amp-hour.  You want 100 hours, so multiple by 10.  Go out and find 10 batteries of the same 12VDC, 12 Amp-hour capacity.  String them together in parallel.  Put them in a metal tray or a concrete trough--something flame-proof.  Provide for adequate venting of hydrogen gas.  Most UPS's can handle low wattage over a long time--it's just that you need more batteries.

The UPS will keep the entire battery array charged and the enlarged battery pack will allow you to run your low wattage load for a long time.  

Do not do this with a high-wattage load, because the UPS will catch fire.  The MOSFET's get very hot during operation with high loads.

Design your battery pack with double overhead margin.  Since batteries age and their capacity diminishes over time, plan on double the run time.  If you need 72 hours, design a battery pack that will last 144 hours.

---

### Post by wirepuller134 on 2011-09-26
Be wary of local electric codes and of course insurance concerns while modifying the UPS. An understanding of NFPA79 would help as well.

Edit part:  Off the top of my head if the devices are 120VAC at 10W for 72 hours, I would recommend nothing smaller than 2200VA.

---

### Post by Paqman on 2011-09-26
> **tgalati4 said:**
> Go out and find 10 batteries of the same 12VDC, 12 Amp-hour capacity.

Don't just get any battery, you want deep-cycle ones. Look into suppliers of off-grid or battery backup solutions. If you use ordinary automotive batteries you'll kill them. Marine ones would probably be acceptable at a pinch.

To supply 10W at 12V you'll need to push out nearly an amp, so you'll need a battery in around the 100Ah range. Plus an inverter charger, obviously. Batteries have a limited lifespan, buying one with significantly more capacity than you need (eg: 150-200Ah) will prolong its life substantially due to the reduced depth of cycling, but you'll probably still need to budget for a new battery every couple of years.

---

### Post by mips on 2011-09-26
> **needhelpplease said:**
> 
We have a warehouse that only gets power from 9-5 M-F.  It would be nice if we had 24/7 power but can't change it; we don't have control over the operations of it.

So from Friday afternoon until Monday morning you need about 66 hours of runtime at 10W?

Have a look at this chart [http://www.apc.com/products/runtime_for_extendedruntime.cfm](http://www.apc.com/products/runtime_for_extendedruntime.cfm)

It starts at 50W but you only need 1/5th of that. So lets say 66hrs/5=13.2hrs.

Look at the chart and find a UPS rated to give you 13.2+ hrs of runtime with a 50W load.

Looks like most of the UPSs with external battery modules will be able to do that for you.

No single UPS & $150 is going to do it for you.

---

