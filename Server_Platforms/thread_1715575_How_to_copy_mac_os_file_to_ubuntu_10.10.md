---
title: "How to copy mac os file to ubuntu 10.10"
date: 2011-03-27
forum: Server Platforms
---

### Post by jnorthr on 2011-03-27
After several days of hard work, i've installed glassfish v3 on my ubuntu system. This will let us deploy java and groovy servlets to the glassfish environment on the server.

From an iMac OS 10.5, i would like to programatically copy servlets from the mac to the ubuntu system. Can only think of using ftp client as i can drive the ftp client from bash scripts and java code.

Are there other options available that we have missed ?
thanx :confused:

---

### Post by rubylaser on 2011-03-27
You could also use scp, rsync, or unison to name a few.  Or even setup a Dropbox folder to keep both ends in sync.

---

