---
title: "Help alesis usb multimix interference/low volume"
date: 2010-09-21
forum: Ubuntu Studio
---

### Post by Grafens on 2010-09-21
I can't get the volume setting right on my setup, I'm using an alesis usb multimix box with headphones.
If I turn up the headphones volume on the alesis to about one third I get a lot of high pitched interference.
I've noticed that the interference begins when I start jack and that the volume meter LED's on the alesis doesn't even show up but the meter readings on zynaddsubfx show that the output is high.
Any help is appreciated.

---

### Post by maghoxfr on 2010-09-23
Have you tried it with any other software other than zyn? There's plenty of soft synths, maybe give other one a try just to check. Maybe there's something with Jack's settings. I have a Multimix 4 usb and this are my settings, I'm using the 2.6.31-10-rt kernel.

---

### Post by eric71 on 2010-09-24
The Multimix will have its own tab when you open the sound preferences from the Gnome volume control applet. It only has one control - PCM, and it is all the way up by default. Turning that down a little may help.

---

### Post by Grafens on 2010-09-26
Thanks for the replies. I changed the jack settings and the latency has come way down to five milliseconds it was nearly fifty milliseconds before, so that's good.
I did a bit of configuring and was able to reduce the interference, don't know exactly how I did it because I did a few things, but it's sorted now. 
Once again thanks for the pointers they helped.

---

### Post by maghoxfr on 2010-09-26
I'm glad it helped, 5 ms it's even better than mine! I recommend you read [this great thread]("http://ubuntuforums.org/showthread.php?t=1543109&goto=newpost") about tweaking ubuntu for better audio performance.

cheers

---

