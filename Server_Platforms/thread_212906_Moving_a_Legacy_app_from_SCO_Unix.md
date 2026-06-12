---
title: "Moving a Legacy app from SCO Unix"
date: 2006-07-10
forum: Server Platforms
---

### Post by TechServsys on 2006-07-10
For my sins I am the administrator of several SCO Unix serviers.  With the self imolation of SCO I am looking to move to a linux server.  I have a legacy app that I need to keep running for another 5 years that is not available in a linux distro.

So here is the question:  Does anyone know if I can run the app under an emulator (or any other way) under Ubunto Linux ?

bill

---

### Post by bwayman on 2006-07-10
What is the app? It must be a good one.:)

---

### Post by TechServsys on 2006-07-11
It is an integrated psychiatric office management system with about 800,000 lines of code.
Lovely system.

---

### Post by lamego on 2006-07-11
If you look on google there are some artifacts to run SCO binaries from Linux, but they look like very old patches to the 2.2.x series. I would seriously start thinking on doing a real port or reimplementation.
What language was the application written with ? Do you have the source code ?

---

