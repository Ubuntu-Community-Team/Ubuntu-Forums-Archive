---
title: "Two Inputs For Audacity/Ardour"
date: 2015-07-08
forum: Ubuntu Studio
---

### Post by Geothermal123 on 2015-07-08
So I know this isn't an ideal audio setup, but I have an analog mic plugged into the mic jack of my laptop and a usb mic. I've been trying to figure out using alsa or jack or something how to be able to record in audacity and/or ardour with these two inputs.

---

### Post by ajgreeny on 2015-07-08
I don't know ardour but audacity is an application I use quite a lot.

It uses pulseaudio to setup the microphone hardware and input gain that is used, so open up Sound Settings from the volume icon in the panel (the app that opens is **pulseaudio-volume-control**), go to Input Devices and you may find all your microphones available in the drop-down box.

---

### Post by dawiba2 on 2015-07-08
I think that, in essence, you're trying to use two different interfaces simultaneously, which I'm not sure will work.

I think Audacity and/or Ardour will only be able to select one input device at a time, so you would only be able to use one mic at a time, as they are both working on different interfaces.

To use more than one mic at a time, you would really need an interface that accepts multiple inputs and mics that would be compatible with that interface.

Sorry not to be more helpful

---

### Post by jejeman on 2015-07-11
You need to dig for ALSA configuration which uses two audio interfaces simultaneously.

---

