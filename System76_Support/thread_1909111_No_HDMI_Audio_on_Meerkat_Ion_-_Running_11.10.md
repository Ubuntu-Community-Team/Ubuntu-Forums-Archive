---
title: "No HDMI Audio on Meerkat Ion - Running 11.10"
date: 2012-01-14
forum: System76 Support
---

### Post by exogenic on 2012-01-14
Hi there, I've been on a whirlwind tour trying to get my Ocelot Box to output HDMI audio.  Picture is outputted fine (and at correct resolution), but there is no audio.

Steps I've taken so far to troubleshoot:
-Unmuted everything in alsamixer and pulseaudio volume control
-Checked the input to my AV receiver works with a Windows laptop and an HD Tuner
-Reinstalled Ubuntu
-Updated the kernel to 3.2
-Tried all available hardware settings in audio settings, analog sound works through headphone jack when set to analog
-Installed proprietary Nvidia driver (Chipset is Nvidia Ion)
-Asked for help in #ubuntu irc channel

When I play video the volume meters move in the pulseaudio settings.  The model of this Meerkat Ion is ment2.

---

### Post by exogenic on 2012-01-14
output of aplay -L:
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by marshmallow1304 on 2012-01-14
What's in your ~/.asoundrc ?

---

### Post by exogenic on 2012-05-29
That file doesn't exist on my system.  Sorry about the thread resurrection, I never did get this working and want to try again.

---

### Post by exogenic on 2012-05-31
I've found I can route the audio through the Optical Audio jack.  I'm going to do that instead.

---

