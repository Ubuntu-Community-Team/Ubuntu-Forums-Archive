---
title: "how to detect digital camera on fluxbox"
date: 2008-07-02
forum: Ubuntu Studio
---

### Post by tanyeun on 2008-07-02
hi all,
I used to use gnome
and it can automatically detect my digital camera(Canon PowerShot A450)
I change my windows manager to fluxbox recently
but it doesn't have this feather
how should I do to make it work?

thx

David

---

### Post by snowpine on 2008-07-02
> **tanyeun said:**
> hi all,
I used to use gnome
and it can automatically detect my digital camera(Canon PowerShot A450)
I change my windows manager to fluxbox recently
but it doesn't have this feather
how should I do to make it work?

thx

David

Hi Tanyeun, I believe the solution is a volume manager such as gnome-volume-manager. You can make it start when you start fluxbox by adding it to ~/.fluxbox/startup

Make sure you read the comment lines in the startup file; they will tell you where to put the command, and also that you need to put an & at the end.

Hope that works!

ps if you still have Ubuntu installed, you should have gnome-volume-manager already; if not, use sudo apt-get install gnome-volume-manager

---

### Post by tanyeun on 2008-07-03
thx snowpine ^^
it worked!

---

### Post by tanyeun on 2010-05-01
I used to use gnome-volume-manager-gthumb to download photos from my camera
but after I upgrade from 8.04 to 8.10
I don't have gnome-volume-manager-gthumb 
and I can't get it from repository as well
anyone know why they took it out
or is there any alternatives for this task?

thx :D

David

---

