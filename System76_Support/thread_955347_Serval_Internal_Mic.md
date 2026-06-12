---
title: "Serval Internal Mic"
date: 2008-10-22
forum: System76 Support
---

### Post by gmh on 2008-10-22
I have a Serval which I have just updated to 8.10 beta. I am happy with the upgrade and it has fixed some niggling problems I had with 8.04. 
I could never get the internal mic to work properly under 8.04. It was very quiet and the audio capture was very scratchy on both Sound Recorder and Skype. It was only just usable. The puzzler here was that when an external mic was used the sound capture was great. I was hoping the upgrade to 8.10 would remedy the problem. Sadly it has not. I have tried every combination of sound capture configuration (Alsa, OSS, Pulse etc) and I just cant get any decent quality capture from the onboard mic. When I plug in an external mic it functions faultlessly.
Anyone have any ideas? It seems like a hardware/driver issue and it appears the problem has been experienced by others on Darter and Pangolin machines.
I have no system 76 drivers installed on the 8.10 installation. I had the latest drivers installed on the 8.04 installation.

Cheers

---

### Post by thomasaaron on 2008-10-22
Which Serval do you have? (Just FYI: You should always specify this, as there several versions of each System76 model, and some have very significant hardware differences.) System > Administration > System76 Driver will tell you.

---

### Post by gmh on 2008-10-22
Sorry about that.

Its a Serval Performance (SER-P4). In Synaptic the 2.22 System 76 driver is installed.

---

### Post by thomasaaron on 2008-10-22
The internal mic on that particular Serval has never worked incredibly well. It's always been kind of static-y.

As best I can tell, it is a deficiency in ALSA. It should eventually improve. But I know you tease it into a little higher quality by playing with the digital and capture sliders.

---

### Post by gmh on 2008-10-22
Thanks Thomas. I figured it had to be something like that. It kinda works and I use it in a pinch but I have a small external mic which I plug in for most VOIP.

---

