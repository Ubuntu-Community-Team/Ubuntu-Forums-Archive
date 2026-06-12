---
title: "RKHunter Warning in /dev/shm"
date: 2008-11-05
forum: Security
---

### Post by horizonuser on 2008-11-05
I have just run an RKHunter --check and a couple of warning have appeared. Does anyone know what this file is: /dev/shm/pulse-shm-4074143664 and why it might be suspicious? I know I can ignore it from warning but I can't figure out why its being flagged....something to do with enhancing application memory resources, but why be flagged?

Its also warning about some /unhide files.....anyone?

---

### Post by hyper_ch on 2008-11-05
goole knows very well what that "file" is: [http://www.google.ch/search?q=%2Fdev%2Fshm%2Fpulse-shm&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a](http://www.google.ch/search?q=%2Fdev%2Fshm%2Fpulse-shm&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a)

---

### Post by horizonuser on 2008-11-05
> **hyper_ch said:**
> goole knows very well what that "file" is: [http://www.google.ch/search?q=%2Fdev%2Fshm%2Fpulse-shm&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a](http://www.google.ch/search?q=%2Fdev%2Fshm%2Fpulse-shm&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a)

Well, I did start there but there isn't that much information on what I asked....Why is it considered suspicious? A lot of posts saying to whitelist it, which I may do, I was just interested in why RKHunter flagged it.

---

### Post by hyper_ch on 2008-11-05
[http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

---

### Post by LinuxGuyInVA on 2009-03-26
> **horizonuser said:**
> I have just run an RKHunter --check and a couple of warning have appeared. Does anyone know what this file is: /dev/shm/pulse-shm-4074143664 and why it might be suspicious? ...

For anyone using Adobe Reader (acroread) 9.x, there are some additional exceptions you may want:

[LIST]
[*][FONT="Courier New"]ALLOWDEVFILE=/dev/shm/sem.ADBE_ReadPrefs_[a-zA-Z]*
[*]ALLOWDEVFILE=/dev/shm/sem.ADBE_REL_[a-zA-Z]*
[*]ALLOWDEVFILE=/dev/shm/sem.ADBE_WritePrefs_[a-zA-Z]*[/FONT]
[/LIST]

I just installed the latest (March 25, 2009) acroread yesterday, and today [FONT="Courier New"]rkhunter[/FONT] complained about three files (semaphores?) in [FONT="Courier New"]/dev/shm[/FONT].  The files are 16 bytes long, mostly zeroed out, and I'm guessing used for settings.

---

### Post by ryniek on 2011-02-05
> /dev/shm/pulse-shm-4074143664

sounds like one of PulseAudio's shared memory processes.

---

### Post by cariboo on 2011-02-05
This is a two year old thread. Closed

---

