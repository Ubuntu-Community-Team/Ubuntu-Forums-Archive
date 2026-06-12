---
title: "microphone recording"
date: 2008-09-10
forum: Ubuntu Studio
---

### Post by Cresho on 2008-09-10
hi!  I managed to get my mic working with some stupid hacks!  I want to know the correct way of getting this thing to work correctly?

this is how I did it.

in the terminal

"asoundconf list"

then it spat out this

asoundconf list
Names of available sound cards:
Audigy2
SAA7134


So then I created a script

#!/bin/bash
sleep 10 && asoundconf set-default-card Audigy2;

and forced executable and forced it to autoboot in sessions under preferences.  Now my sound recorder works and I can record from mic no problem but audacity still sucks.  How can I Fix my problem?

---

### Post by billgoldberg on 2008-09-10
> **Cresho said:**
> hi!  I managed to get my mic working with some stupid hacks!  I want to know the correct way of getting this thing to work correctly?

this is how I did it.

in the terminal

"asoundconf list"

then it spat out this

asoundconf list
Names of available sound cards:
Audigy2
SAA7134


So then I created a script

#!/bin/bash
sleep 10 && asoundconf set-default-card Audigy2;

and forced executable and forced it to autoboot in sessions under preferences.  Now my sound recorder works and I can record from mic no problem but audacity still sucks.  How can I Fix my problem?

You might like asoundconf-gtk better.  :p

Try installing the newest audacity from it's website.

Also, I think it can only do ALSA, do you use ALSA?

---

### Post by Cresho on 2008-09-10
thanks!  i just installed the asoundconf-gtk.  Does this prioritize bootup?  or do I need to force select each time?  I tride audacity latest but it crashes.  Ill see if the new one works for this current setup.

---

### Post by Cresho on 2008-09-11
Hey that method works!  Thanks!

---

