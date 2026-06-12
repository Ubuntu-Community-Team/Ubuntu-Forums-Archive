---
title: "sudo shutdown ..."
date: 2009-04-17
forum: Server Platforms
---

### Post by boondocks on 2009-04-17
On a Ubuntu server, I want to setup a user "goodbye" with a limited privilege.
The ONLY thing "goodbye" can do is shutdown this Ubuntu server.

In fact, as soon as "goodbye" logs into the console:
= The system will initiate shutdown.
= sudo shutdown -h now

How can I do this?

---

### Post by kerry_s on 2009-04-17
just put "halt" in the bottom of ~/.profile.

---

### Post by sisco311 on 2009-04-17
add *goodbye* to the sudoers file.
[uhelp]community/Sudoers[/uhelp]

```
goodby ALL=(ALL) NOPASSWD: /sbin/halt
```

and put "sudo halt" in the ~/profile file.

---

