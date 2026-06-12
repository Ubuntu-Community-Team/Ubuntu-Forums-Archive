---
title: "usb mouse &amp; touchpads"
date: 2016-04-03
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-04-03
It's common if using a usb mouse to disable the touchpad. However if the mouse is removed or dies then proper behavior would be for the touchpad to be re-enabled.
That was prior behavior in Gnome/Ubuntu, no longer..
[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1540561](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1540561)

---

### Post by vasa1 on 2016-04-03
I used Lubuntu 16.04 via a plain Live USB and a Live USB with persistence. In both, I had a mouse attached via USB cable to my laptop and both the mouse and touchpad were functional. I didn't try unplugging the mouse.

To my mind, there is no difference between Lubuntu 14.04 and Lubuntu 16.04 in this regard.
```
06:56 AM ~ $ uname -a
Linux vasa1-Inspiron-1545 3.13.0-83-generic #127-Ubuntu SMP Fri Mar 11 00:25:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
06:56 AM ~ $ 

```

---

### Post by mc4man on 2016-04-03
> **vasa1 said:**
> I used Lubuntu 16.04 via a plain Live USB and a Live USB with persistence. In both, I had a mouse attached via USB cable to my laptop and both the mouse and touchpad were functional. I didn't try unplugging the mouse.


The way it worked/works in gnome is this - 
By default the touchpad is enabled.
When connecting a usb mouse, (wired or wireless), it becomes active & the touchpad remains active
The user disables the touchpad so they're  just using mouse.

If they remove the mouse or it disconnects for whatever reason -  
the old behavior was to immediately re-enable the touchpad
the new behavior is the touchpad remains disabled so no mouse/cursor, ect.

---

