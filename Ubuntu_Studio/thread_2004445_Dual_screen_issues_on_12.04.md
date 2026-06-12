---
title: "Dual screen issues on 12.04"
date: 2012-06-15
forum: Ubuntu Studio
---

### Post by Ali_Barba on 2012-06-15
Hello, 

I got Ubuntu Studio 12.04 LTS 32-bit edition installed on my machine, with an Ati HD4350 graphics card (512MB DDR2 video RAM), to which two identical monitors are connected. 

I just wanted to report that the whole graphics setup seems to be very buggy. First of all, I got two screens to chose from for set up of resolution, refresh rate etc., although just one of them was actually powered up, the other one being in standby. I usually use one monitor only for surfing and casual work, and when I have real work to do I switch on the second monitor to have more screen real estate to work with. 

So though one of them was on standby, it was still the default one offered for setup in the system options screen. Not realizing which was which, I changed the settings there, which led to funny results (desktop being shown in a sort of overlay mode, windows exceeding monitor space) and a system crash. Only after several reboots did I figure out that I had to adjust the second screen. 

But then again, it would only work out correctly when I set BOTH screens to the same resolution! Otherwise I would get display errors. 

I also tried installing the Ati proprietary drivers, but as soon as I reboot and try to install the driver update package (there are currently two - one main package and the update pack), I get an error message and both driver packs show as disabled. Though I can still select Catalyst after a reboot, but only the user version - the admin version will not even start up when clicked. 

All that looks like it needed some work ...



PS: I did not try to fire up the second monitor yet, since I was already glad to finally having been able to set my desired resolution and refresh rate for one monitor, and did not want to mess with the graphics setup any further for the moment.

---

### Post by jejeman on 2012-06-16
With radeon driver active, make the setups you want with xrandr. Then save them in ARandR gui application, and switch beetwen them in there.

Allegedly ARandR should help you setup screens, but it doesn't, but it can save profiles which you can use.

---

