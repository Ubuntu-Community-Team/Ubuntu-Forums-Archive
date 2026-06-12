---
title: "Background Hisses during &quot;silent&quot; recording"
date: 2012-12-20
forum: Ubuntu Studio
---

### Post by Alecossy on 2012-12-20
Hey there, today I tried recording a small jam session using JACK and Ardour on my laptop and noticed that there was some background noises. 
I decided to unplug everything and run a silent recording to see if that sound came from my setup or from JACK/Ardour itself and even that recording had noise in it.
Hisses can be heard even by using ardour in monitor mode.

This is my JACK config screen, what do you guys think the problem might be?
[JACK configuration panel]("http://i47.tinypic.com/312ixye.png")

---

### Post by dannyboy79 on 2012-12-20
is your mic boost set to high in alsamixer?

---

### Post by Alecossy on 2012-12-20
Nope, mic boost is set to zero in alsamixer, already checked that

---

### Post by dannyboy79 on 2012-12-21
not sure to be honest. maybe try turning down your capture setting within alsamixer.

---

### Post by CrocoDuck on 2012-12-21
Hi. Is your soundcard an internal integrated card? In this case the noise you hear could be electromagnetic noise that the card captures, as it is mounted inside the pc (most of the noise is common to be related to the computer's power supply and some kind of ground loop). Some choice of sample rate could result in noise too.

---

### Post by cwsnyder on 2012-12-21
You could also be hearing the 'sampling noise' from changing the analog input to digital, then back to analog.  If you want completely 'silent' recording, you will need specially built and shielded, all analog recording.

---

### Post by cortman on 2012-12-21
This is more a patch than a solution, but what I've always done was edit the final product in Audacity. Just take a complete silent recording of the "noise", then use Audacity's "remove noise" function to grab a sample of that background noise and remove it from the original track.

---

