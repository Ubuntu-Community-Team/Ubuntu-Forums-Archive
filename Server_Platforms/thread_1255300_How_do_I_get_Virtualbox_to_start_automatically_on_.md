---
title: "How do I get Virtualbox to start automatically on boot?"
date: 2009-09-01
forum: Server Platforms
---

### Post by CyberCowboy on 2009-09-01
Hey just starting to virtualize some of my servers and running into a problem.

I've got a Ubuntu server 9.04 host with the closed source VirtualBox 3.0 on it.  When I type in VBoxHeadless -startvm "Server Name" through an ssh session the VM starts and I can get into it no problem.  How do I get that command to run automatically on boot up?

---

### Post by drave on 2009-09-01
add that line to /etc/rc.local

---

### Post by CyberCowboy on 2009-09-01
Just adding that line doesn't seem to work.

---

### Post by drave on 2009-09-01
did you put in the FULL path to VBoxHeadless? It ran Yes?

can you see any sort of error message?

---

