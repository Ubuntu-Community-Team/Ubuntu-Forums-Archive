---
title: "Ynhub with wine"
date: 2007-08-15
forum: Server Platforms
---

### Post by Ntweat on 2007-08-15
I tried running ynhub using wine but i cud not as its showed that the port  

411 was in use (this is the default port for DC++ connections) but on checking this port was free any ideas how it can be solved....

Here is the log of ynhub

[22:49:15] Hub started
[22:49:15] Failed to start listening on port 411, port may be inuse
[22:49:15] Failed to start listening on port 23, port may be inuse
[22:49:15] Listening on port 1411 started successfully
[22:49:15] Application started

---

### Post by applegrew on 2007-08-16
It seems that maybe wine is responsible for this problem. I tried making Apache listen to port 411 and it did. While YnHub run by wine can't. It can only be confirmed if we run another exe file with wine and make it listen to port 411 and it fails too.

---

### Post by applegrew on 2007-08-16
Wooo. I never knew that in Linux u need to have root priviledge to listen to ports below 1024. Hence start  ynhub as

sudo wine "path to YnHub/YnHub.exe"
:oops:
I was trying to do this thing myself since yesterday and was very perplexed.](*,)

---

