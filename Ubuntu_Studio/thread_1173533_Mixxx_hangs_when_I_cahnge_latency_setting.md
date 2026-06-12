---
title: "Mixxx hangs when I cahnge latency setting"
date: 2009-05-29
forum: Ubuntu Studio
---

### Post by RobertWaelder on 2009-05-29
I'm using a Behringer U-Control as an external sound card on an HP Pavilion dv9000, using Mixxx version 1.6.1. The model of u-control im using is the uca202, under Ubuntu Linux 9.04. My Numark TTX-1 turntable is hooked into the line-in of the U-Control. I basically just plugged in the usb soundcard and started using it, not a whole lot of setup involved. But maybe I need special drivers? Most everything works fine in Mixxx, except for the fact that when I change the latency in Preferences and close the dialog, Mixxx hangs. I have to use kill to stop mixxx. when I run mixxx from the console and try to change the latency, the error message in the console says Segmentation fault:

```

    Debug: SoundDevicePortAudio::open() "4, USB Audio CODEC : USB Audio (hw:1,0)"
    Debug: m_dSampleRate 44100
    Debug: iLatencyMSec: 49
    Debug: output channels: 2 | input channels: 2
    Debug: iLatencySamples: 4324
    Debug: iLatencyMSec: 49
    Debug: Opening stream with id 4
    Debug: Opened PortAudio stream successfully... starting
    Debug: Dynamically loaded PortAudio library!
    Debug: PortAudio: Started stream successfully
    Debug: iNumDevicesOpenedForOutput: 2
    Debug: iNumDevicesOpenedForInput: 1
    Segmentation fault

```

What is going on? Is there a way to change the settings in a config file? I'm noticing a few other issues as well. First, it is extremely unstable. The audio engine just seems to poop out after a few songs and the waveform display stops, even though the record is still spinning. Second, is there an easy way to bypass the timecode and switch over to classic vinyl?

---

