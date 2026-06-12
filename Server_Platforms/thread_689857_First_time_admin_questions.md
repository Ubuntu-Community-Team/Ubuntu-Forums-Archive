---
title: "First time admin questions"
date: 2008-02-06
forum: Server Platforms
---

### Post by prem1er on 2008-02-06
I'm running Ubuntu Server from home and I have a few questions about permissions.  For now it is just a file server that I want my friends to have access to through SSH.  I want to create a permission system that when anyone else (besides me) logs in can only access their folder to write to, but be able to read from everyone else.  Each user will have their personal directory, under /home/users/.. .   When they log on through SSH I want them to be in the /home/users directory and not have access to any files above that.  So I guess that is the first part of my question.  How do I specify the folder that users get logged into when they first access the server?

---

### Post by insineratehymn on 2008-02-06
Hey, prem1er.

You say first time... you up for a challenge?

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

Try that out, it may be a good time.

---

