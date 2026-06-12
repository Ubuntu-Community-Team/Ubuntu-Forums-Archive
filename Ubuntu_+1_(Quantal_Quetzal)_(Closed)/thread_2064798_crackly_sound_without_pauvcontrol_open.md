---
title: "crackly sound without pauvcontrol open"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Steeperton on 2012-09-30
I get a strange fuzz of noise before the login screen appears, and before the desktop appears after login. 

Sound is also generally accompanied with a fuzz.

However, if pauvcontrol is open (even without amending any option), the fuzz disappears!

---

### Post by Steeperton on 2012-10-01
Right, I've narrowed it down to pulseaudio being at fault. Killing it off, and using ALSA is mostly fine - volume is correct, and no crackling.

Pulseaudio has always worked on this machine on all version of Ubuntu up to this one, so I need to dig into the changes made between 12.04 and 12.10...

edit: syslog says this when using clementine and the crackling starts paulseaudio changes the volume, etc.

```

Oct  1 17:06:04 mark-desktop rtkit-daemon[1922]: Successfully made thread 27972 of process 27972 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 17:06:04 mark-desktop rtkit-daemon[1922]: Supervising 2 threads of 2 processes of 1 users.
Oct  1 17:06:04 mark-desktop pulseaudio[27972]: [pulseaudio] pid.c: Daemon already running.
Oct  1 17:06:04 mark-desktop rtkit-daemon[1922]: Successfully made thread 27978 of process 27978 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 17:06:04 mark-desktop rtkit-daemon[1922]: Supervising 1 threads of 1 processes of 1 users.
Oct  1 17:06:04 mark-desktop pulseaudio[27978]: [pulseaudio] alsa-mixer.c: Volume element Speaker has 8 channels. That's too much! I can't handle that!
Oct  1 17:06:05  pulseaudio[27978]: last message repeated 3 times
Oct  1 17:06:05 mark-desktop rtkit-daemon[1922]: Successfully made thread 27982 of process 27978 (n/a) owned by '1000' RT at priority 5.
Oct  1 17:06:05 mark-desktop rtkit-daemon[1922]: Supervising 2 threads of 1 processes of 1 users.
Oct  1 17:06:05 mark-desktop kernel: [27224.410140] delay: estimated 0, actual 352
Oct  1 17:06:05 mark-desktop rtkit-daemon[1922]: Successfully made thread 27983 of process 27978 (n/a) owned by '1000' RT at priority 5.
Oct  1 17:06:05 mark-desktop kernel: [27224.418128] delay: estimated 353, actual 705
Oct  1 17:06:05 mark-desktop rtkit-daemon[1922]: Supervising 3 threads of 1 processes of 1 users.
Oct  1 17:06:05 mark-desktop pulseaudio[27978]: [pulseaudio] conf-parser.c: [/usr/share/applications/clementine.desktop:18] Invalid section header.
Oct  1 17:06:05 mark-desktop pulseaudio[27978]: [pulseaudio] module-augment-properties.c: Failed to parse .desktop file /usr/share/applications/clementine.desktop.

```

killit and respawn, and it's fine for anywhere between 5 minutes and 2 hours...

---

