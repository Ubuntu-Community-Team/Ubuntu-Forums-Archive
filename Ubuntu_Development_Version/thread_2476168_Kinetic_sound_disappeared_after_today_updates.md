---
title: "Kinetic sound disappeared after today updates"
date: 2022-06-18
forum: Ubuntu Development Version
---

### Post by corradoventu on 2022-06-18
i noticed the problem yesterday on two desktops and today it appeared on the laptop after updates
[https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/1979113](https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/1979113)

---

### Post by Frogs Hair on 2022-06-18
I have sound , but it is broken up and muted. Using the pipewire ppa in Ubuntu Budgie.

---

### Post by zika on 2022-06-19
I do not have time to write, now, so I'll state URLs that helped me a while ago when going to Wire:
[https://askubuntu.com/questions/1333404/how-to-replace-pulseaudio-with-pipewire-on-ubuntu-21-04](https://askubuntu.com/questions/1333404/how-to-replace-pulseaudio-with-pipewire-on-ubuntu-21-04)
[https://ubuntuhandbook.org/index.php/2021/05/install-latest-pipewire-ppa-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2021/05/install-latest-pipewire-ppa-ubuntu-20-04/)
Key is to decide which one You want and clean other (PulseAudio and Wireplumber/Pipewire).
Hope it helps, it did it for me. Beware that volume control is a bit tricky and is not yet fully implemented.

---

### Post by Frogs Hair on 2022-06-19
Problem gone after logging in this morning with no other action.

---

### Post by corradoventu on 2022-06-20
I still have the problem on both my desktop and on my laptop, all with Ubuntu Kinetic.

---

### Post by vicshrike on 2022-06-20
Worked for me.


[https://github.com/rollingrhinoremix/docs/wiki/Sound-not-working](https://github.com/rollingrhinoremix/docs/wiki/Sound-not-working)

---

### Post by corradoventu on 2022-06-21
Problem solved on my Ubuntu 22.10 installing wireplumber as suggested in bug: [https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/1979113](https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/1979113)

---

### Post by guiverc on 2022-06-21
Firstly I'll say thank you for your testing, reporting issues, and helping make Ubuntu better, as well as to others reporting on this thread :P

I've **not** noticed any changes, though I only reboot this box about once per ~*fornight*, and I'm on day four, so if it's low-level (*anywhere near kernel*) issue, I'll be running code older than your report on my primary box.  

I've also not used GNOME/Xfce/MATE (*my usual GTKs*) in the last 2-3 days, so no GTK3 environment, but only Lubuntu/LXQt desktop so I'm using *different* higher-level software stack, but I suspect the desktop may not make a difference.

I've not noticed any issues with Lubuntu's dailies in the last 2-3 days; in my own *limited* testing, but also testing by others in the team (*though install testing won't find this issue anyway*), but it could also be related to hardware in use, rather than all devices.

---

