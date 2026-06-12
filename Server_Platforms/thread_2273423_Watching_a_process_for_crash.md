---
title: "Watching a process for crash"
date: 2015-04-13
forum: Server Platforms
---

### Post by LonelyStar on 2015-04-13
Hey,

I am running an ubuntu server in which a java based game server is started.
Is there a software solution to watch the java process for crashes, that can send me a mail when it happens and restart the process?

I have only found things like apport, which (if I understand correctly) is made for watching every process on desktop, not a specific one in a server.

Thanks!
Nathan

---

### Post by Lars Noodén on 2015-04-13
For 12.04 and 14.04 you could set up something in [upstart](http://upstart.ubuntu.com/cookbook/).  That's how most daemons are managed.

---

### Post by tgalati4 on 2015-04-14
Run it via an ssh terminal and simply watch the terminal output.  Usually JAVA crashes are obvious.  You can use the *-verbose* switch to get more output.

---

### Post by LonelyStar on 2015-04-27
I am now using "monit" which sends emails if a process does not exist anymore.

---

