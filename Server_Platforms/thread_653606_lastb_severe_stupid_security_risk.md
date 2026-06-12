---
title: "lastb: severe stupid security risk"
date: 2007-12-30
forum: Server Platforms
---

### Post by esagherardo on 2007-12-30
I ran by chance in this severe security risk involving the files  /var/log/btmp and /var/log/wtmp, where init/login/getty record succesful and bad login attempts (these files are browsed by last, lastb).

The bad thing is that, in many distributions  (e.g. gutsy as well as an old debian/sarge), these files are created world-readable. 

A common user's mistake is to insert the password in the place of the login. Usually, one immediately after logs in correctly. Hence there are two subsequent entries very close in time in the two files, where the first user (in btmp) is the password, and the second user (in wtmp) is the corresponding username.

I discovered this because I was terrified by seeing my root password displayed by a lastb, so I checked the access permissions of the files. :-(

---

