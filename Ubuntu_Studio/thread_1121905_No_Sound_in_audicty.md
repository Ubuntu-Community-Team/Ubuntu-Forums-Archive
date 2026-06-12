---
title: "No Sound in audicty"
date: 2009-04-10
forum: Ubuntu Studio
---

### Post by Foxfire on 2009-04-10
when I import files I get no sound but they play in Movie player ect  the files are mp3

---

### Post by cotcot on 2009-04-11
Have you installed libmp3lame and enabled audacity to read mp3 ?

Audacity is one of the apps that in some installations cannot use the sound server if the sound server is already used by another app. If you cannot hear mp3 but you can hear other formats this is not an issue in your installation. If you do not get sound with any audio format log out and log in and start audacity as first application to check this.

(I removed all pulseaudio related packages, so i only have alsa left. Since then this kind of problems is solved. Same for blender)

---

