---
title: "Pulse Audio problem: &quot;no output devices available&quot;"
date: 2017-10-17
forum: Ubuntu Development Version
---

### Post by Dread Knight on 2017-10-17
I've upgraded from 17.04 to 17.10 the other day and I don't have any sound devices listed anymore, even though the sound actually works.

> dread@FreezingMoon:~$ start-pulseaudio-x11 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
dread@FreezingMoon:~$ 


The devices are lacking in both Gnome-Shell and KDE...
Any help or ideas on how to debug / solve this would be greatly appreciated!

---

### Post by Dread Knight on 2017-10-17
Apparently sound works, it's just that KDE doesn't list any of the audio devices, sigh.
Which really sucks, as I can't switch to headsets and Gnome-Shell is not starting up for me either. Hopefully I won't run into issues with my neighbors yet again xD
Trying to connect to my bluetooth headset also fails.

---

### Post by ventsislav-mladenov on 2017-10-19
Why this is marked as solved ? The sound is working but still I get no output or input found. No mixing is available or other functionality through the widget.

---

### Post by caryb on 2017-10-19
Mine is broken too have spent hours trying to fix this

---

### Post by cariboo on 2017-10-20
Closed, as this thread is marked solved, and Artful has been released.

---

