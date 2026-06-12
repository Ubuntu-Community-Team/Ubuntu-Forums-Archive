---
title: "[SOLVED] Virtualbox Audio"
date: 2008-05-10
forum: Virtualisation
---

### Post by MNICY on 2008-05-10
I have Virtualbox 1.6.0 installed on Ubuntu 8.04. I used the Ubuntu 8.04 deb package to install it.
Im using the audio in Ubuntu and Virtualbox

This is the problem: 
if i am playing music (in ubuntu), i get this error:
```

No audio devices could be opened. Selecting the NULL audio backend with the consequence that no sound is audible..


Error ID: 
HostAudioNotResponding
Severity: 
Warning


```As the error says, Audio does not work in the virtual machine.

However, if Ubuntu is not using Audio, the virtual audio works, but then Ubuntu is unable to play any audio.

Anyone know the problem?

---

### Post by MNICY on 2008-05-10
anyone?

---

### Post by MNICY on 2008-05-11
Solved it :)

You have to select PulseAudio in the Virutalbox settings if you using ubuntu 8.04.

(just posting in case someone has the same problem)

---

### Post by djgrant on 2008-08-19
For me, PulseAudio didn't work but ALSA did.

---

