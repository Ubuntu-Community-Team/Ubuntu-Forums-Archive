---
title: "guest additions problem?"
date: 2008-07-28
forum: Virtualisation
---

### Post by wsamh on 2008-07-28
Does anyone know where can I download a copy of guestadditons 1.5.6 or 1.6.0. Everytime I install the current guest additions, my screen resolution gets scruwed up and none of the features like "shared folders" and "usb" does not work. If there is a way to get 1.6.3 working. Let me know.

---

### Post by Fire_Chief on 2008-07-28
The guest additions are usually included with the version of Virtualbox you are running.

Also, are you running 1.6.2? There is no 1.6.3 out at the moment that I can find.

Are you running the OSE version or the binary version from Sun?

Cheers!

---

### Post by wsamh on 2008-07-28
i'm sorry. I meant to say 1.6.2. I'm at work, so I could not remember the version. It is the version that comes with virtualbox, and yes, I am running the binary version from sun. I'm using windows xp as my guest os.

---

### Post by Fire_Chief on 2008-07-28
I am also running 1.6.2 with an XP Pro guest. I was able to setup a shared folder pointing to my home directory on Ubuntu with no problems. I did not get USB to mount my flash drive in the XP guest though. Per the docs, it seems the account running Virtualbox needs read/write permission to the usbfs though I'm not sure if that's referring to the actual mount point or a device driver in the system.

---

