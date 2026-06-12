---
title: "TouchPad at isa0060/serio4/input0 lost sync at byte 1"
date: 2008-03-03
forum: System76 Support
---

### Post by ackey on 2008-03-03
Every once in a while (but often enough that I need to fix it) my mouse stops responding then usually begins acting weird.  After it stabilizes some it is still MUCH more responsive that previous.  I'm running Kubuntu (Gutsy) on DarU2.  Last time, this happened about twice in a row.  dmesg output:

```
[12069.720000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12069.720000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12069.720000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12069.720000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12069.724000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12069.724000] psmouse.c: issuing reconnect request
[12072.500000] ipw3945: Microcode SW error detected.  Restarting.
[12073.016000] ipw3945: Microcode HW error detected.  Restarting.
[12074.048000] ipw3945: Can't stop Rx DMA.
[12075.140000] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[12075.404000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[12078.372000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[12078.404000] input: SynPS/2 Synaptics TouchPad as /class/input/input7
[12110.344000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12110.344000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12110.344000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12110.344000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12110.348000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[12110.348000] psmouse.c: issuing reconnect request
[12114.220000] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[12114.768000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[12114.796000] input: SynPS/2 Synaptics TouchPad as /class/input/input8
```

I've found some things mentioned here: [http://ubuntuforums.org/showthread.php?t=134123&page=2](http://ubuntuforums.org/showthread.php?t=134123&page=2) but I wasn't sure if they were applicable or not.  Whenever this happens and I have firefox open I see some strange message about turning carets on (something about pressing F7 and some different mouse behavior).

---

### Post by thomasaaron on 2008-03-03
Could you please see if it does this with an Ubuntu (not Kubuntu) live CD? If it does, contact me at supprot(at)system76.com.

---

### Post by ackey on 2008-03-14
Running on Ubuntu (gutsy) I still have the "lost sync" problem, but not the associated behavior.

dmesg:
```
[   87.572000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   87.584000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.

```

I'm not sure what is causing the "lost sync" but at least in Ubuntu it is barely noticeable.  KDE must have a problem with the resync.  

It looks like I'm coming back to Gnome!

---

### Post by thomasaaron on 2008-03-14
Those messages are indicative of a bad touchpad. To verify, I need you to duplicate the problem on a live CD.

---

### Post by dpecile on 2008-03-20
try to add  i8042.nomux=1 as kernel option. 
Fixed the bug in a lenovo c200.

---

