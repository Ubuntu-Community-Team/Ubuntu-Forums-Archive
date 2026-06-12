---
title: "Need help with mixer in Ardour"
date: 2010-01-29
forum: Ubuntu Studio
---

### Post by xislayorcsx on 2010-01-29
Okay, so I have a Behringer 22 channel mixer that is plugged into my U Control USB adapter. I've recorded through this mixer in Audacity before, but can't seem to get it to work in Ardour. I read a post about someone trying to record with a USB mic in Ardour and had to set it up with JACK. I'm not sure how to get the mixer to work though. :-k Any ideas?

---

### Post by robeast on 2010-01-29
Are you running the JACK sound server? If not then installing qjackctl (the graphical front end for it) is the first step...with potentially many more steps to follow. However, you can use ALSA in Ardour, which is most likely the driver that Audacity was using.

---

