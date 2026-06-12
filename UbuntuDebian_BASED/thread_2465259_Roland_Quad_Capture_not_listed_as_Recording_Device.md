---
title: "Roland Quad Capture not listed as Recording Device"
date: 2021-07-27
forum: Ubuntu/Debian BASED
---

### Post by Daniel_Coffey on 2021-07-27
OS : Pop!_OS 21.04
Gnome : 3.38.5
Hardware : Intel i7-7700K, 32Gb 3000MHz CAS15, nVidia GTX 1080ti

Audio Interface : Roland Quad-Capture (USB-B)

ISSUE : Device not displayed in the list of Recording Devices on Settings - Sound - Input

Hello folks - I remember that when I last tried Linux Mint about five years ago that the Roland Quad Capture was not well supported in Linux at the time. I am now back trying to use Linux again and while the playback side of the Roland is now well supported, I cannot select it as a Recording device and would appreciate some assistance finding out why.

The list of Output devices does show it properly as "Analogue Output - QUAD-CAPTURE" but the Input devices only shows a 3.5mm jack device built into a soundbar I have.

Oddly enough, however, the Quad-Capture is listed by the "arecord -l" command and I would love to know the reason why I cannot select it.

Output of "aplay -l" snipped to hide irrelevant items...

```
daniel@caselabs-s8:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: QUADCAPTURE [QUAD-CAPTURE], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The output of "aplay -L" gives more options...

```
hw:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Direct hardware device without any conversions
plughw:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Hardware device with all software conversions
sysdefault:CARD=QUADCAPTURE
    QUAD-CAPTURE, USB Audio
    Default Audio Device
front:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Front output / input
surround21:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Direct sample mixing device
usbstream:CARD=QUADCAPTURE
    QUAD-CAPTURE
    USB Stream Output
```

Now for "arecord -l"...

```
card 1: QUADCAPTURE [QUAD-CAPTURE], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And "arecord -L"...

```
hw:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Direct hardware device without any conversions
plughw:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Hardware device with all software conversions
sysdefault:CARD=QUADCAPTURE
    QUAD-CAPTURE, USB Audio
    Default Audio Device
front:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Front output / input
dsnoop:CARD=QUADCAPTURE,DEV=0
    QUAD-CAPTURE, USB Audio
    Direct sample snooping device
usbstream:CARD=QUADCAPTURE
    QUAD-CAPTURE
    USB Stream Output
```

It is showing in arecord but I would love to know the reason why it is not selectable on the Settings - Sound page. Is there a dependency missing or is it still as unsupported as it was back in 2017 when I last looked?

---

### Post by howefield on 2021-07-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Daniel_Coffey on 2021-08-03
Assistance no longer required as I have replaced the device with a Focusrite Scarlett Solo 3rd Gen which works correctly out of the box.

---

