---
title: "Static with headset microphone"
date: 2009-09-07
forum: System76 Support
---

### Post by ajlewis2 on 2009-09-07
I have Daru1 with Jaunty fresh install.  I had this problem long ago, but it disappeared along the way with upgrades or using KDE.  

I plug in a headset after a fresh boot.  The sound produced from the microphone has static.  If I open the mixer and change option to Front Mic and then back to Mic, the static disappears.

I do have the switches set to Headphone at all times.  I have all settings on Pulse Audio. I have installed System76 drivers.  

It seems like after boot and before I monkey with the mixer, I have both mics working and the static is coming from the Front Mic.  Can I turn off the Front mic to see?

Under Recording in the mixer, what does "Toggle auto recording from capture" mean?

Thanks.

---

### Post by thomasaaron on 2009-09-07
Try muting the various mic options. Sounds like some sort of feedback.

---

### Post by ajlewis2 on 2009-09-07
Muted the front mic in the mixer and the boost on both mic and front mic. The background is still there.

I verified that what is happening is that both the external and internal microphones are capturing when I plug in the external mic.  I did this by putting sound into both mics while doing the sound capture test. 

After I click the capture option from Mic to Front Mic and back to Mic, the sound is captured only in the external mic.

I did find a kernel bug on up to 2.6.30 where plugging in an external mic does not disengage the internal mic; so I assume that is where the problem lies.  I did not find a fix.  And now I can't find the link to the bug. 

I'll just do the change from one mic to the other in the mixer when I need to use it.  Hopefully it will go away again like it did before. :-)

---

