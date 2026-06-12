---
title: "Bottom of Screen Cut Off - Starcraft"
date: 2009-06-23
forum: Wine
---

### Post by Tcc242 on 2009-06-23
Trying to play Starcraft and the bottom inch or so of the screen is being cut off. Running Ubuntu 9.04 with a resolution of 1280 x 800.

1)Wine Version: 1.0.1
2)Terminal Output:
```
tcc@wine /media/HULLO/SC/SCUSB.exe
tcc@tcc-laptop:~$ fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f420,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8

```3)Wine Config: Everything is at its default values


Here's a Pic of what I see (taken from phone), as you can see the bottom is cut off
[IMG]http://mail.google.com/mail/?ui=2&ik=dda360664c&view=att&th=1220fd8dc8498da0&attid=0.1&disp=inline&zw[/IMG]

---

### Post by NightMKoder on 2009-06-23
You have a widescreen resolution - I don't think starcraft knows what that is. There's been threads about this and I believe you need to change your resolution to 1024x768 or start a new X server with that resolution.

Regardless - update to the latest wine (1.1.24) and see if it helps.

---

