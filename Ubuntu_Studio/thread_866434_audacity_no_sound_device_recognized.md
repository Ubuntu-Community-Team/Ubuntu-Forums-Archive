---
title: "audacity no sound device recognized"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by tom kersey on 2008-07-21
have amd mobile sempron laptop with on board sound.
my sound players work but audacity does not.
no record, no playback.
no matter what parameters i put in for the sound device i always get the error that says error opening sound device check sample rate, etc.
tried every option -- no change.
sound card is via 8235.
any help?
:(

---

### Post by odius on 2008-07-21
Hey, try installing Jack Control and start it while Auddacity is not running. After Jack Control starts run Audacity again.

Works for me, good luck.

---

### Post by Creative2 on 2008-07-23
i am not sure but it's very important to install :


```
sudo apt-get install sox libsox-fmt-all 
```

then test with this 
```

rec testfile.wav ; play testfile.wav
```

of course use mixer to set yuor mic's volume...

if doesn't works i think is a driver problem

---

### Post by unoodles on 2008-07-23
You are affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/203837](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/203837)

The way I get around it is after starting audacity I run the command:
kill `pgrep jackd`

---

### Post by thorgal on 2008-07-23
maybe instead of killing jackd, you could open Audacity's preferences window and select ALSA as the audio backend so Audacity does not start jackd when you fire it up ?

---

