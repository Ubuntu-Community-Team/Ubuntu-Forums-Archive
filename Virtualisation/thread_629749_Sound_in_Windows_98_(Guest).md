---
title: "Sound in Windows 98 (Guest)"
date: 2007-12-02
forum: Virtualisation
---

### Post by MI123645 on 2007-12-02
Hey guys, I'm running Ubuntu Gutsy on the host, and I have a really weird problem with sound. Most sounds work in win98, but when I play MIDI files, the music plays slow. It also effects the program playing the music as well. If I turn off the music, the program goes fast. 

Any solutions? Also, anyway I can have sound on both the host and guest machine?

---

### Post by insane_alien on 2007-12-03
what virtualisation software are you using?

---

### Post by MI123645 on 2007-12-05
I'm using VMware. I'm thinking it may have something to do with Ubuntu rather than Windows.

---

### Post by insane_alien on 2007-12-05
is sound working in ubuntu? if so then ubuntu is not at fault.

okay, the soundcard that VMware emulates probably isn't one of the preinstalled drivers on win98. see if you can force windows to tell you and then find and install the driver from the net.

---

### Post by MI123645 on 2007-12-06
I already did that, which allowed me to play normal wav files correctly but not MIDI files. They sound extremely slow, but if I load something, they sound extremely fast. If only I can control the sound of the MIDI somehow....

Anyways, I cannot thank you enough for trying to help me.

---

