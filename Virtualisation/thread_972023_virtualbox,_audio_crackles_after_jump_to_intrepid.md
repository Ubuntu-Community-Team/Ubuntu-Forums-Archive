---
title: "virtualbox, audio crackles after jump to intrepid"
date: 2008-11-05
forum: Virtualisation
---

### Post by leutnant on 2008-11-05
The audio worked fine in hardy, but ever since I upgraded to Intrepid, the sound on the guest XP VM crackles. Is this a problem with virtualbox or my setup? 

Btw, My host driver is ALSA and Controller is ICH AC97

---

### Post by FrostyFlames on 2008-11-06
Use the Pulse host driver. ALSA crackles like you said and OSS just doesn't even work.

---

### Post by leutnant on 2008-11-06
Thanks, I'll try that and post back.

---

### Post by wersdaluv on 2008-11-07
With the same settings, I have no sound at all. i think, the guest Windows XP needs a driver for the pulseaudio

[[img]http://xs233.xs.to/xs233/08455/screenshot709.png[/img]](http://xs.to)

---

### Post by dnns on 2008-11-16
I tried that to no avail, every option (OSS, ALSA, Pulse) works but the crackles, pops, choppiness, noise is still the same.

Would love to fix that. Soundblaster 16 not recognized in Vista guest with Ubuntu 8.10 host (Virtualbox 2.04)

Anybody else ideas?

---

### Post by Martin Rabson on 2009-09-02
bump!
Ubuntu 9.04 Host 64 bit
XP 64 bit Guest
VirtualBox 3 Guest Addition installed
PulseAudio / ALSA / OSS
Sound scratchy broken, tried all settings combinations.

Ubuntu 9.04 Host 64 bit
_XP 32 bit Guest_
VirtualBox 3 Guest Addition installed
Sound now ok, so it was 64 bit XP causing the issue

---

### Post by VMSandman on 2009-09-10
Have you tried swapping out the audio hardware.

It sounds like a driver issue but then again it could be faulty hardware.

---

### Post by wynneth on 2009-10-03
BUMP!

Ubuntu 9.10 host
Windows XP guest

Onboard audio (laptop).

Tried every combination just like previous posters and still getting crackling sound.

---

### Post by Pengwyn44 on 2009-10-09
Lots of people on forums, including me, report the problem with audio when running XP as guest on Ubuntu 9.04. It cannot be a hardware problem because all our hardware will be different. My machine is brand new. My voice input also crackles and XP will not play CDs nor CD files copied to the hard drive. Yet it plays it own sounds perfectly including Media Player sample files.

---

### Post by DouglasAWh on 2010-01-05
I have a no audio issue with Win7.  It's a Fedora host, but GOOG sent me here.  I've tried all three and just updated to the newest VirtualBox on the VB website.

---

