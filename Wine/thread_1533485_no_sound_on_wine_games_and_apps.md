---
title: "no sound on wine games and apps"
date: 2010-07-18
forum: Wine
---

### Post by norseman-has-a-laptop on 2010-07-18
i was playing one of my games and well i noticed there was no sound so i turned up my speakers still no sound i went to the desktop unmuted the sound lol but yet no sound when i played the game so anyone help me please thank you
-fritz

---

### Post by asdfoo on 2010-07-22
try updating to Wine-1.2

if it still has no sound, maybe pulseaudio is interfering, try suspending it or killing it

---

### Post by soldier1st on 2010-07-22
go to wine/configure/audio and under directsound/hardware acceleration change it to emulation from full.

---

### Post by norseman-has-a-laptop on 2010-07-23
awesome thank ill tell you if it works or not

---

### Post by norseman-has-a-laptop on 2010-07-24
ok so now i know this thread is for sound but i have one other problem 

when i pause the game for like 10 minutes or so i come back and its sometimes just locks up the system 
it has happened often but after i upgraded to 10.04 it happens very little but still happens

---

### Post by c7borg on 2011-01-18
> **soldier1st said:**
> go to wine/configure/audio and under directsound/hardware acceleration change it to emulation from full.

That did it for me on uosecondage using wine on 10.10

cheers!!

---

