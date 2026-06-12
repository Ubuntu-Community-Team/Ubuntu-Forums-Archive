---
title: "Sound conflicts in 13.04"
date: 2013-08-21
forum: Ubuntu Studio
---

### Post by tonapc on 2013-08-21
Hello!
I am a music teacher and I am teaching a course based on Ubuntu studio. I have 13.04 freshly installed for the year on over 40 computers. I have noticed a conflict when switching between Hydrogen (without Jack, in Auto mode) and browser based audio and video, such as youtube and podcast streams. Either one will work fine in a fresh reboot, but once both have been active at the same time, they both crap out. I have gotten some workarounds (close browser and hydrogen, restart hydrogen) but in years past I have not had an issue running non-jack audio applications over web audio. 

With my teacher's computer I actually have to reboot before I can get a youtube video to play if I have opened hydrogen. 
Any suggestions?

Thanks guys,
Abe

---

### Post by jejeman on 2013-08-21
What happends when you kill/start pulseaudio?

---

### Post by tonapc on 2013-08-21
The error occurs after Hydrogen has been opened - Youtube/browser based audio stops working. If I close Hydrogen and kill pulseaudio, nothing changes in the browser, sound still does not work. Pulseaudio restarts automatically, right?

---

### Post by jejeman on 2013-08-21
Does other applications work? Media players etc.
Is Hydrogen using pulseaudio or ALSA direct? Is Hydrogen really dead?

Yes, pusleaudio deamon auto respawns.

---

