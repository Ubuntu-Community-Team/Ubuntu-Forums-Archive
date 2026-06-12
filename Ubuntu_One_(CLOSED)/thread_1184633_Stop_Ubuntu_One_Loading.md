---
title: "Stop Ubuntu One Loading"
date: 2009-06-11
forum: Ubuntu One (CLOSED)
---

### Post by celticbhoy on 2009-06-11
Is it possible to stop Ubuntu One load on star-up, I don't want to remove it, just stop it starting when I log in. I realise that it is still under development, but my PC becomes unusable due to CPU cycles & memory being hogged.

---

### Post by cb951303 on 2009-06-11
> **celticbhoy said:**
> Is it possible to stop Ubuntu One load on star-up, I don't want to remove it, just stop it starting when I log in. I realise that it is still under development, but my PC becomes unusable due to CPU cycles & memory being hogged.

have you checked "Menu>System>Preferences>Startup Applications"
although I'm not sure, it may be there...

---

### Post by celticbhoy on 2009-06-11
Only part of it rests there, the syncdeamon which is the bit that causes the problems doesn't.

---

### Post by joshuahoover on 2009-06-11
> **celticbhoy said:**
> Only part of it rests there, the syncdeamon which is the bit that causes the problems doesn't.

Unfortunately, you can't stop the ubuntuone-syncdaemon from starting up automatically currently. Our Nautilus extension starts the ubuntuone-syncdaemon, so you're not able to stop the daemon from running separately.

---

### Post by eilios on 2009-06-11
If you _really_ want to, make a shell script that kills the syncdemon and put it to load after nautilus.

---

### Post by celticbhoy on 2009-06-11
Its ok folks, I have just been killing the process's in sys monitor. I was just wondering if it could be set, but as it is still early in development I will put up with it.

---

### Post by eilios on 2009-06-11
> **celticbhoy said:**
> Its ok folks, I have just been killing the process's in sys monitor. I was just wondering if it could be set, but as it is still early in development I will put up with it.
 > **eilios said:**
> If you _really_ want to, make a shell script that kills the syncdemon and put it to load after nautilus.
 
This should do what you ask.

---

### Post by fejao on 2010-07-09
@celticbhoy:
To answer this and many questions of what is missing by default in ubuntu theres always Ubuntu-Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

@eilios: Schönes web gumpel

---

