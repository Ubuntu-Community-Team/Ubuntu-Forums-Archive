---
title: "High Power Usage."
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by donniezazen on 2012-03-24
Hi,

I just did a clean install of 12.04 Live. Power Usage seems to be running very high over 20W. The only thing I am running is Chromium.

```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1 vt.handoff=7
``` I have this in my grub line along with ALPM and terminal blink fix from [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

I have TLP and Thinkfan installed. I have cranked up the temperature limit by 3C, so, it does not trigger fan at a low temp such as 50C.

```
#  Syntax:
#  (LEVEL, LOW, HIGH)
#  LEVEL is the fan level to use (0-7 with thinkpad_acpi)
#  LOW is the temperature at which to step down to the previous level
#  HIGH is the temperature at which to step up to the next level
#  All numbers are integers.
#

# I use this on my T61p:
#sensor /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

(0,	0,	58)
(1,	51,	63)
(2,	53,	64)
(3,	55,	66)
(4,	59,	68)
(5,	62,	69)
(7,	65,	32767)
```

Thank you.

---

### Post by SheamusPatt on 2012-03-26
How's your CPU consumption? Are there any busy processes running?

I'm asking because I've noticed compiz chewing up significant resources when using the Unity 3D desktop (Unity 2D, which doesn't use compiz, seems much better). I'd imagine that on a laptop, CPU hogs would translate into extra power.

---

### Post by rtalcott on 2012-03-26
Been watching my laptop with 12.04...seems to me chrome/chromium suck a LOT more power than Firefox...this is a recent observation and it may be incorrect but try using FF and see what happens..

rt

---

### Post by donniezazen on 2012-03-26
> **SheamusPatt said:**
> How's your CPU consumption? Are there any busy processes running?

I'm asking because I've noticed compiz chewing up significant resources when using the Unity 3D desktop (Unity 2D, which doesn't use compiz, seems much better). I'd imagine that on a laptop, CPU hogs would translate into extra power.

At the time, I did the clean install and only ran Chromium. You are right about Compiz, it indeed is taking at least 10% of CPU.

> **rtalcott said:**
> Been watching my laptop with 12.04...seems to me chrome/chromium suck a LOT more power than Firefox...this is a recent observation and it may be incorrect but try using FF and see what happens..

rt

I have noticed that too. FF seems to be much light on memory and CPU compared to Chromium. As soon as I start Chromium temp cranks up by 5-10 degrees.

---

