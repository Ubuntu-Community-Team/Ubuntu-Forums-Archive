---
title: "Root user built-in protections???"
date: 2010-01-30
forum: Security
---

### Post by Moozillaaa on 2010-01-30
Any Linux machine (except PCLOS) that I log into as root user seems to not start networking.

I haven't tried sudo /etc/init.d/networking restart , to see if it does start, because anytime I DO this, it's for 'local' work.

Anybody know about default root user configuration settings???

---

### Post by movieman on 2010-01-31
Do you mean booting single user? That won't start many services at all, since it's intended for system recovery after some serious fault so it provides a minimal environment for repair.

---

### Post by OpSecShellshock on 2010-01-31
From a best practices standpoint it is inadvisable to give a direct root session network access. Best to log in as a user and elevate for whatever task requires it. I wouldn't know how to change the configuration to allow root to have network access, but I would advise that if you find out how to do it, and if it's necessary for a specific task, that you change it back whenever the task is finished.

---

