---
title: "MIDI Sync not working well at all"
date: 2014-04-30
forum: Ubuntu Studio
---

### Post by Karl_Ekdahl on 2014-04-30
Recently i've had some quite severe problems syncing my computer to MIDI clock coming from external hardware devices, i have tried two different pieces of software (Renoie & QTractor) and they both report a fluctuating incoming clock from 110 - 160 BPM for a incoming 120 BPM clock  - all other MIDI in/out works it seems. This issue didn't come up until a few weeks ago, i have relied on incoming MIDI sync for playing shows for almost a year before this started happening.

I'm getting the same results both on a Midiman Uno and a Midiman 2x2 (both USB), i've tried it with Ubuntu 12.04, Ubuntu studio 13.04 and a fresh install of Ubuntu studio 14.04 - same result. As i've had a few USB issues in the past i was considering the possibility of a hardware issue and tried it on another laptop running Xubuntu 11.10 with no change. I even monitored the USB traffic to the device with wireshark and while i did see a few malformed packets in the initialization of the device, it seems to communicate flawlessly once up and running (though i'm def. not a USB expert).

I've tried poking around with various options in Jack, and also tried running the softwares with bare alsa support - again, no change. I also tried using the midisport-firmware package, though my devices are both working - they just don't sync, and hence, no change.

At this point i'm at a complete loss as to what the issue could be, i'm still fairly new to linux so any help would be greatly appreciated!

Btw. this is my first post in these forums.

---

### Post by n5jyk on 2014-05-27
If you tried the midi device on a different computer and it still shows bpm fluctuations, I'm suspect the midi device's clock might be the issue. If its possible with the midi devices you have, set the fluctuating clock device to external clock and either put it in the middle of the midi chain or let the computer generate the clock for the midi bus. Please post again if still having trouble after implementing this, or if you have trouble sourcing an external clock. You might share your setup including model and firmware version of each midi device and how it is connected to the midi bus.

Come back and mark this thread solved with a little explination of how it was solved. 

Be well and happy,

-b

---

