---
title: "Samba Timestamps issue"
date: 2020-09-11
forum: Server Platforms
---

### Post by greggex on 2020-09-11
I have recently noticed an issue with the timestamps on files copied to the server via Samba. All three timestamps get set to the current time.

I've tried copying with Dolphin, "cp -p" and "cp --preserve=timestamps"
Tried from Manjaro and Lubuntu clients.
Tried updating server to HWE (5.4) kernel

The shares are mounted using mount.cifs
 I'm currently running 18.04.5 - The issue seems to have started in the last month or so. 

Anyone else experiencing the same?

---

