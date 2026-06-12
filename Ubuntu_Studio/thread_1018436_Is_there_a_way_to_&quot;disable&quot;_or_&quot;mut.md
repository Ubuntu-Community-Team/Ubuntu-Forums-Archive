---
title: "Is there a way to &quot;disable&quot; or &quot;mute&quot; the second speaker in one-channel audio?"
date: 2008-12-22
forum: Ubuntu Studio
---

### Post by Julita on 2008-12-22
On video there are two people speaking simultaneously, and the voice of one of them is louder. Unfortunately, I need to know what says another person. I can hear only separate words, but I need desperately to know his full speech. Is there a way to divide one-channel audio so that I can hear the whole part of it?

---

### Post by Julita on 2008-12-22
up

---

### Post by Julita on 2008-12-31
up

---

### Post by glotz on 2008-12-31
Try going to system > prefs > volume control and there click the little chain link icon below the master volume control to disconnect left and right speaker volume and then pull the other slider way up and the other way down.

---

### Post by namdung on 2008-12-31
In *Synaptic Package Manager*, install **alsamixergui** or type in terminal
```
 sudo apt-get install alsamixergui
```

Launch from *Applications-->Sound & Video-->Alsamixergui* or type in terminal
```
alsamixergui
```.

Now look for the speaker icon and on top of *Front* and select either the left or right channel for single channel sound output.

---

