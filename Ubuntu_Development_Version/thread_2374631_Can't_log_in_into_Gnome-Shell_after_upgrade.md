---
title: "Can't log in into Gnome-Shell after upgrade"
date: 2017-10-17
forum: Ubuntu Development Version
---

### Post by Dread Knight on 2017-10-17
I've upgraded from 17.04 to 17.10 and when I log-in, Gnome-shell won't start and I get taken back to the log-in screen.

Any ideas on how to debug / solve this would be greatly appreciated.

---

### Post by DogMatix on 2017-10-17
Have you tried logging in to the 'Ubuntu on Xorg' session?

---

### Post by Dread Knight on 2017-10-17
> **DogMatix said:**
> Have you tried logging in to the 'Ubuntu on Xorg' session?

There was no such option displayed for me, but `Gnome on Xorg` I think.

---

### Post by DogMatix on 2017-10-17
I have a 17.10 install and in gdm I have options 'Ubuntu' (Wayland) and 'Ubuntu on Xorg'. Maybe its because you have updated rather than installed from scratch! 
Will Gnome-shell start if you select 'Gnome on Xorg'?

---

### Post by Frogs Hair on 2017-10-17
If you have a working session such as unity log in and run the update manager. If you had the gnome-shell as a second session there may be conflicts being that ubuntu and ubuntu on xorg are now gnome-shell sessions.

---

### Post by Dread Knight on 2017-10-17
> **DogMatix said:**
> I have a 17.10 install and in gdm I have options 'Ubuntu' (Wayland) and 'Ubuntu on Xorg'. Maybe its because you have updated rather than installed from scratch! 
Will Gnome-shell start if you select 'Gnome on Xorg'?
Perhaps. That's my single Gnome related session, hence why I'm here.

> **Frogs Hair said:**
> If you have a working session such as unity log in and run the update manager. If you had the gnome-shell as a second session there may be conflicts being that ubuntu and ubuntu on xorg are now gnome-shell sessions.

I actually have KDE installed since before (but it has its own issues, sigh) and I'm currently using it, especially to do updates from time to time, hoping that all the issues will eventually get fixed...
Maybe, though I had Unity removed long time ago afaik, because I wasn't very fond of it. Anyway, this gives me an idea, will try reinstalling ubuntu-desktop package, even if it pulls in a lot of extra bogus stuff...

---

### Post by Frogs Hair on 2017-10-17
Make sure ubuntu-session is installed. You may do better with a backup and clean installation. 

> This package contains the required components for running a GNOME 3 session
with default Ubuntu configuration, based on the GNOME Shell.

---

### Post by DogMatix on 2017-10-17
What display manager are you currently using? Is it GDM?

---

### Post by Dread Knight on 2017-10-17
> **DogMatix said:**
> What display manager are you currently using? Is it GDM?

Using the default purple/pinkish one, whichever one is nowadays, as they swapped them quite a few times...

Anyway, installing ubuntu-desktop package did the job for me, will mark this as solved and move to the next issues at hand...

---

### Post by wildmanne39 on 2017-10-20
Thread closed since it is solved and 17.10 has been released!

---

