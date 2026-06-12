---
title: "wine+pulseaudio=freeze"
date: 2010-01-20
forum: Wine
---

### Post by dino99 on 2010-01-20
since a week or so, wine 1.1.36 + pulseaudio (0.9.22~ *) come in general freeze:
~ 80% cpu
~ gnome-setting-daemon crash randomly due to "not enough memory" on a system with q9550 + 4go.

Have to remove ubuntu-desktop & purge all pulseaudio packages to have a stable system.

Is anyone else having such trouble ?

---

### Post by dino99 on 2010-01-20
Actual wine is very stable & this problem only appear with the last pulseaudio updates few days ago. Of course, when wine is updated , winecfg is updated too each time. Looking at system-monitor: pulseaudio and gnome-setting-daemon have a too heavy cpu activity and that freeze an application and slow down all the system.

As logs don't show errors about that, i even don't know exactly what package or dependency create this problem: even when it complaint about missing memory, system-monitor still show lot of free memory not used.

So, is system-monitor showing wrong informations ?

note: same problem with Karmic and Lucid

---

### Post by dino99 on 2010-01-20
ok , got it

after removing/purging then reinstalling alsa/pulseaudio, i still have the same problem. Configuring sound device & output doesn't help.
But i have seen some mixed devices: digital & analog ( i only have analog).

So, i have deleted the hidden files : .pulse & .gstream*, then reboot.

Bingo, sound is perfect now.

---

### Post by dino99 on 2010-01-20
one boot later, same problems again.



can't use metatrader with wine due to this alsa problem:

alsa plug-in [wine preloader] freeze wine and hide mouse on active windows: huge cpu activity on pulseaudio and gnome-setting-daemon.

Googling around, some users says to deselect alsa and choose esound instead, what i have done in winecfg, then kill pulseaudio.
Wine work better but is very slow with this sound choice. Choising esound or oss does not help much.

Removing/purging alsa/pulseaudio then reinstall them does not work, erasing .pulse neither, nothing special in logs.

This is test on Lucid with wine 1.1.36 that was well working 2 weeks ago before last alsa upgrades.

---

