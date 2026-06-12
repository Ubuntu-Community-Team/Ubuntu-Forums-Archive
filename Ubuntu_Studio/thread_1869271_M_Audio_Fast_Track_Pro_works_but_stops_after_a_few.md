---
title: "M Audio Fast Track Pro works but stops after a few seconds"
date: 2011-10-25
forum: Ubuntu Studio
---

### Post by Jay105 on 2011-10-25
hi,
 
i have been setting up alsa on my new 11.10 partition and have managed  to get the M Audio Fast Track Pro working. When testing it initially  (using youtube) i got playback and it sounded great. When i clicked on  another video firefox crashed and all sound stopped working. Then in the  terminal my fast track was no longer recognized. i went through the  whole process again and ran into the exact same problem for a second  time.
 
Any Help?

---

### Post by sgx on 2011-10-26
Hi, it might be a conflict with pulseaudio grabbing the sound.
Use the command

ps ux


to list running processes while a youtube is playing.
If anything with pulse in the name is listed, try the command

killall pulseaudio

and reload the youtube.

Maybe have firefox use xine or mplayer plugin for video output.
Synaptic should have a package for that. You can use synaptic to
remove pulse and libpulse etc.

For audio setup in qjackctl, see the other maudio topic nearby.
Cheers

---

