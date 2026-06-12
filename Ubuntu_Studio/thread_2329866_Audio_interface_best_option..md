---
title: "Audio interface best option."
date: 2016-07-05
forum: Ubuntu Studio
---

### Post by Mickeyj4j on 2016-07-05
Hi i have a Belkin TuneStudio. This is a small 4 channel mixer with a USB audio interface built in. 

to set it up I have run QjackCtl when i plug the Belkin in it comes up with 2 options.

1. hw:CODEC USB Audio CODEC (hw:2)
2. hw:CODEC,0 USB Audio CODEC (hw:2,0)

using both will not record 
1. Audacity: This will not pick up the device.
2. Ardour: This will detect the audio coming into the channel and stop and start when I turn my mp3 player off. When i press the record button to record the detected audio it just flashed from grey to red and nothing is recorded. 

Where am i going wrong with these to simple enough apps. and QjackCtl

thanks for all the help in advance. 

P.S. yes i am a new user of ubuntu studio but i have used audacity in the past to record things in a normal os using a usb mi c and audio input without jack or low latency.

---

### Post by CrocoDuck on 2016-07-06
Hi!

Give us the outputs of these two commands:

```

aplay -l
arecord -l

```

Also, as you said you are new, I would suggest to read [this article]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack").

> **Mickeyj4j said:**
> 
... in a normal os ...


:lolflag: what's not *normal* about Linux? Don't worry, I understand it has a learning curve, especially for audio. I remember it very well...

---

