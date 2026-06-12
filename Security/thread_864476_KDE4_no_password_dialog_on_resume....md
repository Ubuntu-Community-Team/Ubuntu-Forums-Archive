---
title: "KDE4 no password dialog on resume..."
date: 2008-07-19
forum: Security
---

### Post by onyxrev on 2008-07-19
Hey Folks,

I couldn't find any information on this in the KDE4 groups.  Whenever I put my laptop to sleep (Suspend to RAM), KDE4 doesn't ask for a password in order to achieve access to the desktop.  I thought that maybe setting a password for the screensaver would help, which works, but does not affect  suspend/resume.

Anyone have any experience with this?  I cannot find a 'password on resume' type checkbox anywhere in the system configuration area.

I am running KDE 4.1RC1 from the official PPA.

Thanks!

---

### Post by jranaya7410 on 2008-12-21
I'm having the same problem. I am using KDE 4.1.3 and when i resume from a suspended session, it does not prompt for a password. The Power Manager has an option to "Lock screen on resume" but this does not do anything.

---

### Post by private_lock on 2009-01-28
The same for my laptop :-(

It won't ask for a password on resume from disk.

Till now I found some people trying to get rid of their password-prompt on resume ... From those I tried to reverse:

My /etc/default/acpi-support is (and was without change):

```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true
```

Moreover the gconf-editor / apps / gnome-power-manager / lock has a check on hibernate and on suspend, though I think KDE won't care about Gnome settings?!?

Last but not least I try to set my screensaver password ... I'll see tomorrow, if this did the trick ...

Good night
private_lock

---

### Post by danmarycap on 2009-03-13
> **private_lock said:**
> The same for my laptop :-(

It won't ask for a password on resume from disk.

Till now I found some people trying to get rid of their password-prompt on resume ... From those I tried to reverse:

My /etc/default/acpi-support is (and was without change):

```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true
```

Moreover the gconf-editor / apps / gnome-power-manager / lock has a check on hibernate and on suspend, though I think KDE won't care about Gnome settings?!?

Last but not least I try to set my screensaver password ... I'll see tomorrow, if this did the trick ...

Good night
private_lock


I'm one of those people trying to get rid of the password prompt on resume from suspend.

When I checked /etc/default/acpi-support, it's just as you said:
```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true
```
so I changed it to "false".  Reboot, suspend, resume...password prompt.  Didn't work.

Anyone know how to disable the password prompt on resume? I'm running Ubuntu 8.10 on a Dell mini9.

-Dan

---

### Post by private_lock on 2009-03-14
Sorry, I forgot to report back:

I solved my issue by clicking on the battery symbol in the tray-area:

On rightclick there is the "Guidance Power Manager", offering me suspend and hibernate. On leftclick a panel with options opens up. There I could set the annoying brightness* and also the password on resume.

That password-switch only works, if the hibernate was triggered via closing the lid. and it somehow managed to kill the suspend and hibernate options from my K-Menue ... but as long as it works on closing the lid I didn't research the issue any further.

Bye
private_lock

PS: * My laptop worked perfectly well the last two years giving me on startup the brightness, it had the last time I turned it of. There was no need for Kubuntu to interfere with. But now, that the software learned how to get its greedy fingers on, it switches to full brightness on every start.

---

