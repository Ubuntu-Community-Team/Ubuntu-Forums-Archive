---
title: "sound issues in VIrtual machine"
date: 2010-01-08
forum: Virtualisation
---

### Post by hyburn on 2010-01-08
hey folks.

I just got my mouse to work in my VM.

ok so Im using virtualbox and running windows. how can I get the sound to work? kinda wanna play some games....

thanks

---

### Post by fouadatmeh on 2010-01-08
Hello,
The following settings in Virtualbox are working great for me:

Host Driver: OSS Audio Driver
Controller:  ICH AC97

---

### Post by becatron on 2010-08-01
I've tried those settings (and every other combination) but I've still had no luck. My windows 7 doesn't recognise that I have an audio device at all...

Any ideas?

---

### Post by Meow27 on 2010-08-01
i dont think virtualbox has any support for DX10.

you may as well try using Wine.

---

### Post by becatron on 2010-08-03
oh, I fixed it by downloading audio drivers from the windows 7 guest :D

---

