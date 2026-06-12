---
title: "Audio input problem with JACK and Behringer UCG102 guitar link"
date: 2011-09-09
forum: Ubuntu Studio
---

### Post by smay on 2011-09-09
**EDIT Appears to be working now. Will mark as solved once I am confident it won't go away.**

Hi,  I have a problem getting sound into the computer with JACK and the  Guitar Link (which I got partly because it was mentioned as  well-supported hardware on the Rakarrack site).

 I can play sound through the headphones port, and also set up the  patchbay with Virtual Keyboard -> Amsynth -> Rakarrack ->  headphones using JACK, so I know that JACK is working with Rakarrack.  

However I can't get sound from the line in. In 'Alsamixer', the Guitar  Link shows as 'USB Audio CODEC' and only has a PCM Playback control, and  no capture control.  

Confusingly, I **am** able to record good sound in Audacity straight from  the ALSA input, so it seems to be a JACK problem?  

OS is Ubuntu 11 Natty Narhwal (with many audio apps installed). Screenshot of JACK configuration:[ http://i.imgur.com/3RGku.png]("http://i.imgur.com/3RGku.png")

Output of aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Output of arecord -l
```

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by jejeman on 2011-09-09
what is the output of
```
arecord -l
```

---

### Post by smay on 2011-09-09
About 5 minutes after I posted it magically started working! The Ubuntu forums really are amazing.

All I did as far as I can tell was install Timemachine, and connect the system output port into the system input port to see if I could hear the guitar, and I could!

I will leave this post here and update it with any information if I can work out exactly why it wasn't working.

---

### Post by sgx on 2011-09-09
Hi, this device should be sending sound via usb, so you need to make sure it is the jackd input device, and that your soundcard or motherboard soundchip, is the output device. In the qjackctl setup panel,

Input device  >
Output device  >

click the  > widgets to see and select the desired sound device for the current session. The device ID hw:0,0 hw:1 etc can vary with different hardware installed/plugged in. qjackctl saves a settings file, .jackdrc
in your /home/username folder

You can craft a few variants and keep them in .bash_history, to start
easily from the terminal, the up-arrow key cycles through the terminal command history.

You can can use timemachine, and a jackd audio player, to overdub,
record a track in timemachine, import, edit and export via audacity, load the track into aqualung player, connect it to timemachine, and also connect your guitar. Press record in timemachine, start playback
in aqualung, set the levels, and have a go. Ardour can be used for
advanced multi-track recordings, videos on youtube.
Cheers

also, your bundled NI software will probably work in a wine wineasio setup. You can run the installer, or if you have a dual boot, copy all
the NI files/folders to their equivalentlocations in
/home/username/.wine

---

