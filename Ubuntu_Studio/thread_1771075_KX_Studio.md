---
title: "KX Studio"
date: 2011-05-30
forum: Ubuntu Studio
---

### Post by wbm on 2011-05-30
I installed KXStudio on my main machine. Fresh install of Kubuntu 11.04, then added all the KXStudio stuff as outlined on the web site.
All went fairly well but there are a few oddities.

E.g. yesterday I placed drum loops at 90bpm and added two guitar tracks. Shut down the machine.
Today, booted machine up and opened same song. Now the song is still 90 bpm, the drums sound the same, but the guitar tracks are almost a whole step lower?!?

A song from my previous install of UbuntuStudio 10.04 sounds a a little more than a half step higher.

I suspect some bit rate issues, but so far I can't figure out how to make the necessary adjustments. Cadence says 44.1, Ardour says 44.1 and that hasn't changed.
Odd

---

### Post by Pablo_F on 2011-05-30
Hi, 

What audio card do you have?

---

### Post by wbm on 2011-05-30
> **Pablo_F said:**
> Hi, 

What audio card do you have?

I use a Tascam US122 (the old original one) USB interface. I have been using that successfully for several years on that same computer using UbuntuStudio.

Oddly enough, today that same song played at regular pitch again.

Every time I restart the computer, or re-log in, KDE asks me to "forget" some input/output devices and drivers etc. It doesn't seem to care one bit if I click "don't ask me again" or not either.

In Cadence and in Jack Control everything is set to 441000.

In order of appearance this is what happens to far:
1. Start up or log in:
web browser launches and connect to Open ID something. Haven't figured out how to turn that off either.

2. KDE tells me Tascam not working
a) it works anyways - e.g. sound plays in YouTube, Rythmbox, Ardour etc. just fine
b) it doesn't (no sound at all)
c) no sound from all applications but I hear startup sound and can play audio from the Dolphin Information side panel.

3. If no sound, then I need to unplug and re-plug my Tascam USB interface, light comes on, then in Cadence I need to switch to Hw: Tascam and then it works

4. If sound is working it is an either / or situation
a) I either get sound from the "Desktop", e.g. a start up sound and I can play audio files in the folder side panels by highlightening an audio file
or,
b) I get sound from everything else but no start up sounds and no sounds from the Dolphin Information side panel.

5. In UbuntuStudio Gnome: when I booted the computer, lights came on on the Tascam USB interface (I never had to touch it).
In Kubuntu/KXStudio, after boot or log in, no lights come on until I pull the USB plug out and put it back in. I guess that is one of the many oddities of KDE.


Note: sound from the Dolphin Information side panel explanation
I have a folder of a bunch of loops. In Gnome hovering over a file plays it. In KDE, selecting it let's me play it in the info side panel.
This is just a quick way for me to browse through and find loops.

---

