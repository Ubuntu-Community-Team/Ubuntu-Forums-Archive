---
title: "change default software when blank disc inserted"
date: 2007-05-29
forum: Ubuntu Christian Edition
---

### Post by kiwidipstick on 2007-05-29
Hi, when I insert a blank disc, serpentine automatically pops up. How can I change this to be K3b please?
Also, how do I change the default Totem to VLC when I insert a video disk or dvd?
Appreciate an answer in simple plain language please for this dipstick please!

Blessings, James.

---

### Post by blackened on 2007-05-29
In Feisty go to System -> Preferences -> Removable Drives and Media.

---

### Post by kiwidipstick on 2007-05-29
> **blackened said:**
> In Feisty go to System -> Preferences -> Removable Drives and Media.
Thanks for that. I had found that much out (sorry for not stating that originally). But once there, I do not know how to point to the software I want. IE, where do they reside.
Blessings, James.

---

### Post by blackened on 2007-05-30
Most of the programs you'll likely want to use reside in /usr/bin.

---

### Post by BoyOfDestiny on 2007-05-30
> **kiwidipstick said:**
> Thanks for that. I had found that much out (sorry for not stating that originally). But once there, I do not know how to point to the software I want. IE, where do they reside.
Blessings, James.

open up a terminal

type

*whereis vlc*

or 

*which vlc* 

Works with any installed app (which is handy if there are multiple binaries)

---

### Post by kiwidipstick on 2007-05-30
> **BoyOfDestiny said:**
> open up a terminal

type

*whereis vlc*

or 

*which vlc* 

Works with any installed app (which is handy if there are multiple binaries)

Thanks BoyOfDestiny, that's a great piece of info for me, appreciate it. James.

---

