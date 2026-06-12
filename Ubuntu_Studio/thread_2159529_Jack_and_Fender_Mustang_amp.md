---
title: "Jack and Fender Mustang amp"
date: 2013-07-03
forum: Ubuntu Studio
---

### Post by Upedro on 2013-07-03
Using Ubuntu Studio 12.04 

I have been trying to record from a Fender Mustang 1 amp thru its usb cable with Jack. I can record the sound coming out of the amp, but in order to do so I lose all output signal. 

In Qjackctl, I can select Mustang amplifier as interface in the setup page, but this cuts all output. I can record the sound from the guitar, but I hear nothing of what I'm doing, and nothing when I play the track.
 If I select Mustang amp as Input, leaving interface and output to default, all I can record is white noise. In this configuration I hear output.
I can change output to HDA Intel, Alc662 analogue or Alc662 Digital, leaving Mustang Amp as input. This allows me to record the guitar, but it kills any output from my DAW (Qtractor). Same thing with Ardour BTW.

I can record the amp (usb) on Audacity without Jack, and everything works fine, input and output normal. 

Why I can't do the same with Jack is beyond me at this point.   

Pierre
Quebec City (CAN)

---

### Post by cub on 2013-07-04
Not a direct answer to your question but perhaps some hints [http://www.linuxjournal.com/content/plug-and-fender-mustang](http://www.linuxjournal.com/content/plug-and-fender-mustang) . Check the comments as well.

Are you sure that Audacity actually did record with Jack and Jack only? I have a vague memory of it using PulseAudio anyway. Check out the long, but interesting thread over at [http://forum.audacityteam.org/viewtopic.php?f=18&t=63419](http://forum.audacityteam.org/viewtopic.php?f=18&t=63419) .

From the Mustang amp specs it should be able to play both input and output, so at least it's possible.

---

