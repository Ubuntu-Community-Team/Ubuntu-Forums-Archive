---
title: "watching multiple videos"
date: 2009-04-02
forum: Ubuntu Studio
---

### Post by wrathkeg on 2009-04-02
Hi, is there any video player which allows for watching (and controlling) multiple videos simultaneously?  I have some scenes recorded on different cameras and would like to be able to watch all of the movies simultaneously.
TIA
WK

---

### Post by Stochastic on 2009-04-02
VLC should work for this if my memory serves correctly.

---

### Post by CraymelCage on 2009-04-02
Smplayer can also do this. Just disable the "Use only one running instance of Smplayer" option in the interface options menu.

---

### Post by wrathkeg on 2009-05-12
Thanks.  I've also discovered that multiple AV files can be combined into a single Matroska file, and that VLC will play these back in such a way that each window is synchronised and controlled from a single set of controls.
```
mkvmerge video1.avi video2.avi audio.wav -o combined.mkv
```

---

