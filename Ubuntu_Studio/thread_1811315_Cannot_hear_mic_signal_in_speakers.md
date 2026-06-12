---
title: "Cannot hear mic signal in speakers"
date: 2011-07-24
forum: Ubuntu Studio
---

### Post by DarkaThal on 2011-07-24
I cannot hear the input/mic signal in the output channel.  In Sound Preferences on the Input tab I can see that the input signal is being detected - the Input Level indicator lights up to show a signal, however I cannot hear this on the output.  I can hear other things (eg. Test Speakers).

---

### Post by jejeman on 2011-07-24
Thats normal. Vu meter is detecting mic sound for recording not for monitoring.
Open alsamixer and unmute playback for mic if you want monitoring.

---

### Post by DarkaThal on 2011-07-24
Sorted.  Thanks very much.

---

