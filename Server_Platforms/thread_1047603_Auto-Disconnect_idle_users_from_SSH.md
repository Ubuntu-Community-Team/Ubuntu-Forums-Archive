---
title: "Auto-Disconnect idle users from SSH"
date: 2009-01-22
forum: Server Platforms
---

### Post by jersak on 2009-01-22
Hi there,
I would like to know if is there a way to reduce the amount of idle time needed for disconeting an user on SSH. I googled a lot but everyone wants to "not disconnect" and the method they use dont works for me.

If someone knows, i would apreciate your share =)

---

### Post by spiderbatdad on 2009-01-22
see: man sshd_config
ClientAliveCountMax
ClientAliveInterval

---

