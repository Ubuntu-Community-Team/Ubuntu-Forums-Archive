---
title: "A weird kernel panic signal, anyone else get it?"
date: 2008-05-13
forum: The Cafe
---

### Post by MONODA on 2008-05-13
When I was using hardy I remember getting full system crashes frequently which wasnt different than gutsy, but I noticed that in hardy when the system would crash, my caps lock key light would begin to flicker (this didnt happen in gutsy). I ignored it. But now I tried to install crux on the same machine (crux lets you compile it from source). When I booted into the system, I got a kernel panic and the light on caps lock key started flickering. Is this just me or do others get this too? it is nice for a dramatic effect ;)

---

### Post by klange on 2008-05-13
panic_blink
It's also supposed to flash the numlock light, but I guess that just doesn't work.

It was made specifically for users in an X server, so that you'd know there was a kernel panic and that it's probably a good idea to hard reboot or something to that effect. Used to get a lot of kernel panics back in late April, haven't had any recently.

There are some ooold patches to the kernel out there that make it blink the kernel panic message in Morse code, any chance getting this in Intrepid? I mean, the flashing is one thing - at least I know it's a kernel panic - but with Morse code you can know exactly what went wrong (if you learn Morse code, that is...)

---

### Post by Sukarn on 2008-05-13
> **WindowsSucks said:**
> panic_blink
It's also supposed to flash the numlock light, but I guess that just doesn't work.

It was made specifically for users in an X server, so that you'd know there was a kernel panic and that it's probably a good idea to hard reboot or something to that effect. Used to get a lot of kernel panics back in late April, haven't had any recently.

There are some ooold patches to the kernel out there that make it blink the kernel panic message in Morse code, any chance getting this in Intrepid? I mean, the flashing is one thing - at least I know it's a kernel panic - but with Morse code you can know exactly what went wrong (if you learn Morse code, that is...)

I can imagine clueless users posting stuff like "my computer is sending strange messages into space!" and "my keyboard is talking to me!!!"

---

### Post by MONODA on 2008-05-13
why not write it to a log instead?

---

### Post by Sukarn on 2008-05-13
> **MONODA said:**
> why not write it to a log instead?

Because disc access will be cut off in most of the cases of kernel panic. The modules for ext3, vfat, etc. would probably be unusable.

---

