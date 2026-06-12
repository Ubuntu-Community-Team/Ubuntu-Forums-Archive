---
title: "TouchPad doesn't work after cold shutdown"
date: 2013-09-28
forum: Ubuntu Development Version
---

### Post by diesel2 on 2013-09-28
Hello,

I have a Lenovo Twist.  The Touchpad doesn't work if I start from a cold shutdown.  It does work if I restart.  from dmesg the differences in the 2 boots are these files are not loaded off a cold start:
```

[   21.221813]  serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd002a3/0x940300/0x126c00, board id: 2253, fw id: 1192539
[   21.288391] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   25.907455] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   21.221827] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   21.288391] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   21.360391]    inputs:
[   28.169132] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input13
```

Also the psmouse module is not loaded.  

In the input devices the Synaptics TouchPad is not there after a cold shutdown.

---

