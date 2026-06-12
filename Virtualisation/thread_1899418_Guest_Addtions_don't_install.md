---
title: "Guest Addtions don't install"
date: 2011-12-23
forum: Virtualisation
---

### Post by seattle vic on 2011-12-23
I'm running Ubuntu 11.10 host and 11.10 guest.  After I received and installed the latest virtualbox upgrade (direct from virtualbox.org), I went to install guest additions, through the usual way (shell, /media/VBox... and then sudo sh ./VboxLinuxAdditions.run

It didn't do anything, just returned a prompt as if I'd simply hit the return key.  No error, no message, nothing.  I even tried it on another 11.10 host computer I have running; same effect.

Anybody else have this issue?

---

### Post by seattle vic on 2011-12-23
I found out on virtualbox.org forums that dkms must be installed for the GE install to work properly.  For some reason it wasn't installed on the 11.10 guest.  Once I installed it, it worked one one of my machines.  On a second computer (again running 11.10 host and guest) it didn't help.

---

### Post by memilanuk on 2011-12-23
Vic,

I've had some wonky results with Virtualbox as supplied by the Ubuntu repositories.  My suggestion would be to uninstall the Ubuntu version, go to virtualbox.org and set up your host system to use the Oracle repos for Virtualbox.  It is all very well documented on their site as to how to go about the process.

After that, on the guest systems you'll typically need more than just dkms installed.  The normal recommendation is to install the build-essential package as well as kernel headers.  Take a look [here]("https://forums.virtualbox.org/viewtopic.php?f=3&t=15679") for a general idea of what you'll need.

HTH,

Monte

---

### Post by seattle vic on 2011-12-23
> **memilanuk said:**
> Vic,

I've had some wonky results with Virtualbox as supplied by the Ubuntu repositories.  My suggestion would be to uninstall the Ubuntu version, go to virtualbox.org and set up your host system to use the Oracle repos for Virtualbox.  It is all very well documented on their site as to how to go about the process.

After that, on the guest systems you'll typically need more than just dkms installed.  The normal recommendation is to install the build-essential package as well as kernel headers.  Take a look [here]("https://forums.virtualbox.org/viewtopic.php?f=3&t=15679") for a general idea of what you'll need.

HTH,

Monte

Thanks Monte.  I installed the essentials and headers on both machines and now neither machine will install GA's.  As before, when I hit return, it just goes to the prompt.

---

