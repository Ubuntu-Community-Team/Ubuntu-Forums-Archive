---
title: "touchpad tapping on acer aspire 8943G"
date: 2010-06-19
forum: Ubuntu One (CLOSED)
---

### Post by mortenbrekk on 2010-06-19
Have anyone been able to disable touchpad tapping on Acer Aspire 8943G.
I am able to turn off the full function of touchpad with xinput or fn+f7 or to disable touchpad tapping and left mouse button at the same time. My hope is to only disable tapping and have the rest working.
Have look at a lot of treads, but I have not been able to find any help.

I have ubuntu 10.04

uname -a
Linux laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux


Here is some nformation from xinput

$ xinput list 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=15    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                     id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

$ xinput list-props "PS/2 Synaptics TouchPad"
Device 'PS/2 Synaptics TouchPad':
    Device Enabled (125):    1
    Device Accel Profile (245):    0
    Device Accel Constant Deceleration (246):    1.000000
    Device Accel Adaptive Deceleration (248 ):    1.000000
    Device Accel Velocity Scaling (249):    10.000000
    Evdev Reopen Attempts (243):    10
    Evdev Axis Inversion (250):    0, 0
    Evdev Axes Swap (252):    0
    Axis Labels (253):    "Rel X" (133), "Rel Y" (134)
    Button Labels (254):    "Button Left" (126), "Button Middle" (127), "Button Right" (128 ), "Button Wheel Up" (129), "Button Wheel Down" (130)
    Evdev Middle Button Emulation (255):    0
    Evdev Middle Button Timeout (256):    50
    Evdev Wheel Emulation (257):    0
    Evdev Wheel Emulation Axes (258 ):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (259):    10
    Evdev Wheel Emulation Timeout (260):    200
    Evdev Wheel Emulation Button (261):    4
    Evdev Drag Lock Buttons (262):    0

---

