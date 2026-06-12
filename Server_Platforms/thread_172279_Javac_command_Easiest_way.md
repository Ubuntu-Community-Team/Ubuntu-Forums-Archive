---
title: "Javac command? Easiest way?"
date: 2006-05-08
forum: Server Platforms
---

### Post by rensu on 2006-05-08
At the moment I have to write long line like this:
/opt/jdk1.5.0_06/bin/javac HelloWorldApp.java
But how I can do that everyone have to write only javac to compile?

---

### Post by rensu on 2006-05-08
Nevermind got my answer.
Just had to write into /etc/profile some lines:
Like this:
export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/lampp/bin:/opt/jdk1.5.0_06/bin/"

---

