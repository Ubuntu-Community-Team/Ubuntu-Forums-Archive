---
title: "Sound Output in VMWare Server"
date: 2010-04-12
forum: Virtualisation
---

### Post by Thund3rstruck on 2010-04-12
This might sound kind of silly but when a VMWare guest executes a task that outputs audio is that audio output to the Host speakers or the Guest speakers (the computer running VMWare Remote Console)?

For example, I have a headless VMWare server which hosts various Linux/Unix, and Microsoft servers and operating systems. Hobbyist developers on my team do most development work through the VMWare remote console. 

I installed VMWare Server on a Ubuntu 9.01 minimal install so there is no alsa or any sound support. However, it occurred to me that the users might still not hear any sound if sound is sent to the host server and not the computer in which the remote console (guest OS) is running?

Can anyone shed some light on this for me? I don't want to mess around with installing sound on this host if its going to pump sound to the host (which has no speakers).

---

### Post by dkyeager on 2010-10-15
bump

---

