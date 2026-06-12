---
title: "Sound problems"
date: 2009-11-06
forum: Ubuntu Studio
---

### Post by mvalviar on 2009-11-06
My sound settings doesn't persist in between boots. My desktop always show up with the audio muted. If I kill pulseaudio for good will I still be able to use other desktop apps?

---

### Post by AutoStatic on 2009-11-06
You could try the following:
[LIST]
[*]Set up the right volume
[*]Open a terminal
[*]Enter the following commands:
```
alsactl store 0 -f Desktop/asound.state
sudo cp /etc/asound.state /etc/asound.state.orig
sudo Desktop/asound.state /etc/asound.state
```
[/LIST]
Now your settings should persist in between boots.

---

### Post by mvalviar on 2009-11-07
It didn't work. The box still boots with muted audio. The thing is there isn't a file named /etc/asound.state. What I did is just copy file there.

---

### Post by AutoStatic on 2009-11-07
> **mvalviar said:**
> It didn't work. The box still boots with muted audio. The thing is there isn't a file named /etc/asound.state. What I did is just copy file there.That's right, the file resides in /var/lib/alsa on Ubuntu. What you could do:
- Make a copy of /var/lib/alsa/asound.state: **sudo cp /var/lib/alsa/asound.state /var/lib/alsa/asound.state.orig**
- Move /etc/asound.state to /var/lib/alsa: **sudo mv /etc/asound.state /var/lib/alsa/asound.state** or simply create a new asound.state file with the command **sudo alsactl store** (after having adjusted your mixer settings)
- Make sure this file gets loaded when you log in by creating a new entry in System - Preferences - startup Applications that contains the command **alsactl restore**

Or you could check it this bugreport at Launchpad: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/315971](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/315971)

---

