---
title: "[SOLVED] Installed programs listing with server."
date: 2006-12-25
forum: Server Platforms
---

### Post by chrismyers on 2006-12-25
Hi there,

I use synaptic with the gui version of Ubuntu, but what are the best ways of listing installed programs with the non-gui server version?

For instance. How would I find out what ftp server I am running? (I know, since I just installed it. But i would like to know how to check).

Cheers in advance.

---

### Post by Rippey on 2006-12-25
try dpkg -l
or if you're looking for someting more specific
dpkg -l | grep "seach"

---

### Post by chrismyers on 2006-12-26
Fantastic. Thats exactly what I wanted.

Cheers :D

---

### Post by Rippey on 2006-12-26
you're welcome :)

---

