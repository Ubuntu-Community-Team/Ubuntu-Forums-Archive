---
title: "wireless off at boot time on panp7"
date: 2011-01-17
forum: System76 Support
---

### Post by tws5 on 2011-01-17
I have a pangolin (panp7) laptop;
wlan0 is disabled by a hardware switch at boot,
so I have to re-enable it by pressing fn+f11 every time
which is quite a bit inconvenient
(but otherwise wireless works just fine).

Since it's a hardware switch, rfkill is not able to override it
(otherwise I would just put rfkill unblock in startup scripts).

I also checked bios settings and couldn't find any relevant options.

Could there be some way to "save" default wireless state via ACPI?

thank you

---

### Post by isantop on 2011-01-18
Actually, it should be persistent across boots, though we have seen issues where, for an unknown reason, the persistence doesn't work. It seems to fix itself after a while, but I'm not sure what's causing it enough to tell you how to get it fixed sooner.

I have seen that it is more common with a dual boot. Are you using a dual-boot setup?

---

### Post by tws5 on 2011-01-23
No, I was using ubuntu installation from system76 (+ upgrades to the last 2010 ubuntu release).

The issue with wireless-off seems to have fixed itself,  after I
(1) attempted to hibernate the laptop with wireless on;
(2) at boot, ignored hibernate image and did a "clean boot".

After doing so, the wireless is always on at boot time.

---

### Post by IAmWhatWasDavidBowman on 2011-01-23
I've seen this before on the mine, but I haven't seen it in a while.

Of course, I sing to my PanP7 from time to time. It seems to like that. ;)

---

### Post by jml on 2011-01-23
I am...

May be you need a different hobby.  ;)

Joe

---

