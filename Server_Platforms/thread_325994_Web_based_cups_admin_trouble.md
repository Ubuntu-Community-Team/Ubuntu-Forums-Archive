---
title: "Web based cups admin trouble"
date: 2006-12-26
forum: Server Platforms
---

### Post by BrandonBrown on 2006-12-26
Hello every one and happy New Year! I just setup the cupsd.config file to were I can access the cups system from a web browser. But for some reason I can't log in to remotely admin the server. It does not take my root password. Also is it a good idea to turn off SSL? I found on a forum that turning SSL off fixes the error message that says upgrade needed. Any ideas?

---

### Post by KenSentMe on 2006-12-28
Can't you login with you default users login and password? It works here.

---

### Post by BrandonBrown on 2006-12-28
Thanks for replying. I have fixed the problem. I found a thread that said to open a terminal and type "adduser cupsys shadow" That fixed my problem. How ever I am still curious if it is a good idea to turn off SSL to fix the error message that says upgrade needed. Is it better to leave SSL on?

---

