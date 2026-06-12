---
title: "No sound after latest update"
date: 2009-10-02
forum: Ubuntu Studio
---

### Post by lament on 2009-10-02
Hey all,

Ubuntu noob here (running Jaunty). I had my sound working fine (through HDMI) until last night's update.

One of these caused the breakage:

Commit Log for Thu Oct  1 22:32:45 2009

Upgraded the following packages:
apport (1.0-0ubuntu5.2) to 1.0-0ubuntu5.4
apport-gtk (1.0-0ubuntu5.2) to 1.0-0ubuntu5.4
libsmbclient (2:3.3.2-1ubuntu3.1) to 2:3.3.2-1ubuntu3.2
libwbclient0 (2:3.3.2-1ubuntu3.1) to 2:3.3.2-1ubuntu3.2
linux-headers-2.6.28-15 (2.6.28-15.49) to 2.6.28-15.52
linux-headers-2.6.28-15-generic (2.6.28-15.49) to 2.6.28-15.52
linux-image-2.6.28-15-generic (2.6.28-15.49) to 2.6.28-15.52
linux-libc-dev (2.6.28-15.49) to 2.6.28-15.52
openoffice.org-base-core (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-calc (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-common (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-core (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-draw (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-emailmerge (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-gnome (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-gtk (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-impress (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-math (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-style-human (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
openoffice.org-writer (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
python-apport (1.0-0ubuntu5.2) to 1.0-0ubuntu5.4
python-problem-report (1.0-0ubuntu5.2) to 1.0-0ubuntu5.4
python-uno (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
samba-common (2:3.3.2-1ubuntu3.1) to 2:3.3.2-1ubuntu3.2
smbclient (2:3.3.2-1ubuntu3.1) to 2:3.3.2-1ubuntu3.2
ttf-opensymbol (1:3.0.1-9ubuntu3) to 1:3.0.1-9ubuntu3.1
uno-libs3 (1.4.1+OOo3.0.1-9ubuntu3) to 1.4.1+OOo3.0.1-9ubuntu3.1
ure (1.4.1+OOo3.0.1-9ubuntu3) to 1.4.1+OOo3.0.1-9ubuntu3.1

aplay -l shows no sound card installed.

Any steps I can take to troubleshoot this would be appreciated.

Thanks!

---

### Post by lament on 2009-10-02
Mods,

Please move to Multimedia & Video.

Well, turns out ALSA was removed somehow with the update. I recompiled and reinstalled 1.0.20 and I'm fine now.

---

