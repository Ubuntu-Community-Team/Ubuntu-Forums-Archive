---
title: "problems with DPS 12 as ardour control surface"
date: 2009-01-19
forum: Ubuntu Studio
---

### Post by musicmatt on 2009-01-19
So here is my situation;

  I am running 8.10 (studio was a bit much this early on) and have Ardour up and running with jack.  I have run into a lot of problems trying to sync my DPS 12 with ardour via midi.  Specifically, I want to be able to use the DPS as a control surface for Ardour, which all the liturature tells me is possible (there is not much as far as I can tell that deals with that combination specifically, but both are supposed to be able to function in the necessary capacity)  .  I can get Ardour to slave to the DPS's MTC without to many problems.  the weird thing is when I try to control the pan and gain parameters via the DPS, the faders all control the wrong things. For example;
DPS                  Ardour
move fader 1 =       toggle mute on track 1
move fader 2 =       toggle solo on track 1
move fader 3 =       actually controls the fader on track 1
move fader 4 =       controls pan of track 1

I can change which track is controlled in this manner by changing the MIDI _IN_ settings on the DPS.

Any thoughts?

---

### Post by musicmatt on 2009-01-22
Ok, Replying to my own post (I figured it out, and figure someoune else might benefit. this will work for any basic midi based control device);
  First, make sure everything is plugged in and turned on, that your external device is exporting either MTC or MMC, and and that Ardour is set to read it. (there is a toggle just to the right of the time clock that by default is set to "internal". click on it and move it to TMC)  Go to make sure the "control surfaces" (under options) is set to "generic midi".  Then, hold down the Ctrl button, and click with the middle mouse button on the parameter you would like to control (gain, pan, ect.) a box will pop up that says "operate controller now".  Move the fader, knob, whatever on your control device, and you're in business. Rinse and repeat.

a helpful link;
[www.64studio.com/book/export/html/208](www.64studio.com/book/export/html/208)  

(for debian, but still good in ubuntu)

---

