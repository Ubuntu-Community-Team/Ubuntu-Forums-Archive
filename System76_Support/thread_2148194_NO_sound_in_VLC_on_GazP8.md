---
title: "NO sound in VLC on GazP8"
date: 2013-05-24
forum: System76 Support
---

### Post by jdwaugh on 2013-05-24
Playing a DVD is proving a difficulty, Videos will not play a DVD, I am not sure if it is because of the Menus or once it said it was the wrong Region?  I wouldn't have thought a player in Linux would ever pay attention to the Region code.  Anyway, I installed VLC, and it plays the DVD but I have no sound.  I tried changing the audio preferences to both Pulse Audio and to Alsa, but nothing helped.

THanks

---

### Post by KlipperKyle on 2013-06-22
Well, the video is playing, so it's not a region code problem. Here are some things you might try:

1. Make sure all the audio codecs are installed <[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)>.
2. Examine your pulseaudio settings with pavucontrol. Pavucontrol is a graphical control panel specifically for pulseaudio. It can be installed by running ```
sudo apt-get install pavucontrol
``` in a terminal.
3. Can you play any stand-alone music? What formats?

---

