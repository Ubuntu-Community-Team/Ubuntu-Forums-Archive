---
title: "For the Life of me: No Sound"
date: 2009-12-06
forum: Ubuntu Moblin Remix
---

### Post by bobbydigital on 2009-12-06
For some reason I can not get sound to work at all and I have tried quite a few methods I have found sifting through this and other various forums, so I think its time for a thread.

I have tried to install the latest Moblin, UNR 9.10, and the latest build of Ubuntu Moblin Remix. Everything is fine, networks picked up A-OK, wireless, bluetooth etc...But zero audio.

My notebook is an LG T1 Express Dual(model# is "T1-7001A9"). Audio works out of the box with Windows 7, and works with Xp after installing the latest driver. 

In windows device manager it says the audio device is Realtek High Definition Audio Device, but Alsa mixer is saying "Intel HDA".

I found this [page]("http://ja.pastebin.ca/raw/1688824"), and it seems to be related, its the same notebook with 9.10, maybe it will provide some light, its over my head. I am not very advanced using Ubuntu (obviously :P)

---

### Post by bobbydigital on 2009-12-06
bump

---

### Post by bobbydigital on 2009-12-07
Bump

Come on someone must be able to help me out :s

---

### Post by gradinaruvasile on 2009-12-07
Open a terminal (press alt+f2 and type gnome-terminal then press enter).
Type in the terminal:

alsamixer

Take a screenshot of that window (alt+printscreen) and post it here.

---

### Post by bobbydigital on 2009-12-07
hera ya, go and thanks for the reply!

---

### Post by gradinaruvasile on 2009-12-08
Sorry for the late reply...
It looks ok. Try unmuting the iec958 - navigate with the arrow keys (right) to the iec958's column and press m.

---

### Post by bobbydigital on 2009-12-08
Tried that but still nothing...hmm

---

### Post by bobbydigital on 2009-12-09
bump

---

### Post by joes7 on 2009-12-10
Are your laptop's built-in speakers activated? If you are unsure, access the Hardware/Driver menu from the "System" menu. If they don't work, try looking at your user permissions. Select "..can use sound devices."

---

### Post by bobbydigital on 2009-12-10
Yes they work, infact last night I booted easypeasy 1.5 (based on Ubuntu 9.04) and had sound. Also it has sound in Windows, which it dual boots.

---

