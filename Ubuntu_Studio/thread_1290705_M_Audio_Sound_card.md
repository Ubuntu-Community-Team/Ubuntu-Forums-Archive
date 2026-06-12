---
title: "M Audio Sound card"
date: 2009-10-13
forum: Ubuntu Studio
---

### Post by deathoftheweb on 2009-10-13
I'm trying to get an M Audio mobile pre USB soundcard to work with Ubuntu 9.04. 

My friend told me to get Jack and Ardour. I tried to download Ardour, but it says that I have packages on my computer that conflict with the installation of that program. 

I also installed Jack, but I'm really clueless on how to make the soundcard talk to the computer. 

Has anyone hooked up M Audio soundcards to Ubuntu? Are there any other methods of recording with Ubuntu? What is the best way to go about recording with the sound card?

---

### Post by sgx on 2009-10-14
Hi, see my post in the Edirol topic nearby, everything should apply to your maudio usb card too!


Also, install libwine, wine, and wineasio, any dependancies, and then install Reaper DAW, [www.cockos.com](www.cockos.com)
This will work very well for multi-track recording and hosting vsts, google for wineasio reaper for lots of details.

Audacity will work for recording, but only appears in qjackcontrol after
you press its record button. So press pause, connect your instrument virtual output to the Audacity virtual input, then press record when you're ready.

zynaddsubfx synth, and rakarrack multi-fx are a powerhouse pair of free
instruments to create and record with.

Cheers

---

