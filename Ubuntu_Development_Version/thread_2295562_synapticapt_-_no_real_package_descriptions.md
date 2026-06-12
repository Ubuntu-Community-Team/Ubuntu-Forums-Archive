---
title: "synaptic/apt - no real package descriptions"
date: 2015-09-19
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-09-19
synaptic continues to fall, gather there is no future for it in Ubuntu
Edit: though in this case not synaptic's fault, have gotten used to the worst with it.
[https://bugs.launchpad.net/apt/+bug/1497626](https://bugs.launchpad.net/apt/+bug/1497626)

---

### Post by Frogs Hair on 2015-09-19
I'm seeing strange behaviour in synaptic. Some programs installed from synaptic are not appearing in dash, but do when installed from the terminal. Some installed packages fail to show up in search which could be description related.

---

### Post by mc4man on 2015-09-19
While synaptic has certainly shown some unwanted behaviour in recent times I'm thinking now this issue isn't from synaptic, something else..
Using the example of vlc;  apt-cache show vlc has just a 1 line - 
Description-en: multimedia player and streamer

If you run the same in 14.04 - 
Description-en: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG-2, MPEG-4,
 DivX, MOV, WMV, QuickTime, WebM, FLAC, MP3, Ogg/Vorbis files, DVDs, VCDs,
 podcasts, and multimedia streams from various network sources.
 .
 VLC can also be used as a streaming server ect, ect.

So possibly in 15.10 only the 1st. line of the debian/control file's Description-XX:  line makes it into the Apt list files, the rest is discarded?

---

### Post by sgage on 2015-09-20
I've noticed this, too. I'd like to see the more informative descriptions come back. And the History feature, as well. I've been using Synaptic forever, and hate to see it dwindling away :(

> **mc4man said:**
> While synaptic has certainly shown some unwanted behaviour in recent times I'm thinking now this issue isn't from synaptic, something else..
Using the example of vlc;  apt-cache show vlc has just a 1 line - 
Description-en: multimedia player and streamer

If you run the same in 14.04 - 
Description-en: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG-2, MPEG-4,
 DivX, MOV, WMV, QuickTime, WebM, FLAC, MP3, Ogg/Vorbis files, DVDs, VCDs,
 podcasts, and multimedia streams from various network sources.
 .
 VLC can also be used as a streaming server ect, ect.

So possibly in 15.10 only the 1st. line of the debian/control file's Description-XX:  line makes it into the Apt list files, the rest is discarded?

---

### Post by mc4man on 2015-09-20
> **sgage said:**
> I've noticed this, too. I'd like to see the more informative descriptions come back. And the History feature, as well. I've been using Synaptic forever, and hate to see it dwindling away :(
The history, (or lack of), is a big deal to me, very useful, organized  & accessible. It's still there though one has to use a root file browser to see the files in /root/.synaptic/log

---

### Post by QDR06VV9 on 2015-09-20
> **sgage said:**
> I've noticed this, too. I'd like to see the more informative descriptions come back. And the History feature, as well. _**I've been using Synaptic forever, and hate to see it dwindling away **_:(
Me Too!
This is about the time when breakage or strange behavior shows up and then gets fixed.
Fingers Crossed

---

### Post by sgage on 2015-09-20
> **mc4man said:**
> The history, (or lack of), is a big deal to me, very useful, organized  & accessible. It's still there though one has to use a root file browser to see the files in /root/.synaptic/log

That's kind of a pain, but at least it's there. Once in a while, it's really good to be able to see the history! Thanks for the pointer...

---

