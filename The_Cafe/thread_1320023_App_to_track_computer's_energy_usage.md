---
title: "App to track computer's energy usage?"
date: 2009-11-08
forum: The Cafe
---

### Post by PhoHammer on 2009-11-08
It seems like I heard about a program that does this in Linux, but I can't seem to find it using
Google or searching synaptic... Any ideas?

---

### Post by handy on 2009-11-09
I was thinking earlier today that it is about time such software became mainstream.

It would be very educational, for me anyway.

Hopefully someone knows of a good app' for the job?

---

### Post by spupy on 2009-11-09
Two things come to mind:
* powertop - Tool that finds the software that makes your laptop use more power than necessary.
* Gnome's power manager has 'power history'. It shows various graphs related to the battery and the power consumption.

---

### Post by Warpnow on 2009-11-09
It won't be very accurate, imho. Not all parts report power usage, do they? Hard drives? Optical Drives?

Plus, the efficiency of your PSU makes a big difference. You are way better off buying a kill-a-watt and hooking it to your PC. It has a setting to record power use over time.

---

### Post by tom66 on 2009-11-09
Laptops usually measure their power consumption. It's available at /proc/acpi/battery/BAT0/state, if the laptop is not charging. It measures power consumption from the battery, so is pretty accurate.

---

### Post by markp1989 on 2009-11-09
> **Warpnow said:**
> It won't be very accurate, imho. Not all parts report power usage, do they? Hard drives? Optical Drives?

Plus, the efficiency of your PSU makes a big difference. You are way better off buying a kill-a-watt and hooking it to your PC. It has a setting to record power use over time.

do they make killawatts that can plug in to your pc via usb for logging??

---

### Post by handy on 2009-11-09
kill-a-watt's are only suitable for the U.S. electricity grid = low volts - high amps.

---

### Post by markp1989 on 2009-11-09
> **handy said:**
> kill-a-watt's are only suitable for the U.S. electricity grid = low volts - high amps.

well its not a kill-a-watt but i have a device that performs the same function on hte uk grid.

---

### Post by Warpnow on 2009-11-09
> **markp1989 said:**
> do they make killawatts that can plug in to your pc via usb for logging??

No, you put it between the wall and your power to measure how much power your computer draws. I don't see why someone would want a usb one?

Its more useful this way, as you are measuring exactly how much power you are drawing from the outlet. Its more foolproof than any other method.

---

### Post by tgalati4 on 2009-11-09
+1 for the killawatt.  I have one and have found that pc's consume:


PIII, 500MHz 66 watts
Celeron, 1 GHz, 46 watts
Pentium D (dual), 3 GHz, 120 watts

Some smart person could come up with a way to make a current loop measuring device that uses the microphone input as the meter and some software to display the instantaneous current consumed and an integrated power (based on input voltage).

I haven't seen any recording USB devices, but there are voltmeters with USB connection.  They are pricey.  Find one with a current clamp and take a power cord and strip open the line lead (typically the black one in a black-white-green power cord).  Integrate the current use in amps over time and multiply by the average voltage and that will give you power consumed over that time.

---

### Post by PhoHammer on 2009-11-09
Thanks for the replies, everybody.
I shall look into this kill-a-watt item...:D

---

### Post by handy on 2009-11-10
> **markp1989 said:**
> well its not a kill-a-watt but i have a device that performs the same function on hte uk grid.

Thanks for all the details!

I need 240v & 10amp, the pin configuration can be dealt with.

---

### Post by handy on 2009-11-10
So, no one knows of a suitable device built to work on the 240volt 10amp household mains system?

---

### Post by markp1989 on 2009-11-10
> **handy said:**
> So, no one knows of a suitable device built to work on the 240volt 10amp household mains system?

this is the one i have 

[http://www.maplin.co.uk/Module.aspx?moduleno=38343](http://www.maplin.co.uk/Module.aspx?moduleno=38343)

---

### Post by squilookle on 2009-11-10
I keep hearing this annoying advert on Spotify from one of the big energy companies (possibly eon? I wasn't paying attention, biut it went something like - uh... oh! uhhh... oh! uhh... oh! and then theres another one where the guy hides the hair dryer to save energy... anyway... ) where they give you some kind of device to measure your energy usage. 

I think it was for the whole house rather than for a specific appliance, and you might have to sign up to get one... but it might be worth a look if nothing else suits... 

Speaking of apps to measure energy usage, (no good for the pc, but interesting) my Android phone got upgraded recently to 1.6 and now has some app that shows which apps on the phone are using the most energy. Not sure how accurate it is yet, but it seems like a good idea. :)

---

### Post by handy on 2009-11-10
> **markp1989 said:**
> this is the one i have 

[http://www.maplin.co.uk/Module.aspx?moduleno=38343](http://www.maplin.co.uk/Module.aspx?moduleno=38343)

Thanks for the reply. :)

After searching a bit, I found the product linked to below. It was designed over here, & has been being produced in Oz since 2005.  Great reviews, so I bought it.  It will help me to accurately understand the usage of electrical appliances in our home, & a few other people's I know also.  

I'm sure that it will eventually pay for itself.

It cost me $285- Oz, (best price I could find) including (free) shipping, on-line from "todae".  I posted that for anyone from Oz that may be interested.

Here's the info' from the manufacturer:

[http://www.power-mate.com.au/](http://www.power-mate.com.au/)

---

