---
title: "How Do I Require A Password To Open Any Application?"
date: 2011-04-01
forum: Security
---

### Post by ald3n3 on 2011-04-01
Is there a way to do this? I disabled the log in screen for my Ubuntu 10.10 for convenience with remote desktop (so the machine starts up right away and connect to vnc). But doing this means anybody at my house can just access my computer and application (brother's friends are a little curious) and they could easily access Keyring and grab all my passwords. So is there a way to require a password everytime an application is opened?

---

### Post by bodhi.zazen on 2011-04-01
Well, physical access is a problem as they could always boot a live CD.

I think your bets option by far is to re-enable login (disable auto login). Otherwise you are sort of chasing your tail, automatic login , but password to access any binaries seems counter productive.

---

### Post by Jive Turkey on 2011-04-01
If you re-enable the login screen you might find X11 forwarding over ssh to be just as useful as vnc (if you only use a linux client).  I haven't been able to get windows to work as a client (yet), supposedly it can be done, I just haven't figured it out yet.

---

### Post by ald3n3 on 2011-04-01
i'll try out x11 when i get home. i have another idea, tell me if it will work. If i enable "require pw when screensaver turns on" would that disconnect my comp from the internet? thus disabling vnc connection? or would it stay connected?

---

### Post by ald3n3 on 2011-04-01
SOLVED
 
I just enabled the screensaver to turn on after 1 min of inactivity. Then enable "require password when screensaver turns on". So a minute after i remotely connect to my computer it locks.

---

### Post by bodhi.zazen on 2011-04-01
> **Jive Turkey said:**
> If you re-enable the login screen you might find X11 forwarding over ssh to be just as useful as vnc (if you only use a linux client).  I haven't been able to get windows to work as a client (yet), supposedly it can be done, I just haven't figured it out yet.

Us Xming on Windows, very straight forward and runs from a flash drive if needed.

---

