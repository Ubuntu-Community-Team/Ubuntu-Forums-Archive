---
title: "Relocating/Mapping var"
date: 2010-01-09
forum: Server Platforms
---

### Post by sarloth on 2010-01-09
I mounted var on a separate partition when I installed my Ubuntu server.

I have since realized this was retarded at best.

Is there anyway to move it back to the root (/) partition from SSH? 

I can give myself physical access to the server by moving my mouse and monitor over to the server, but I don't want to if I don't have to.

Thanks in advance if anyone can help :popcorn:

---

### Post by kidders on 2010-01-10
Hi there,

> **sarloth said:**
> I can give myself physical access to the server by moving my mouse and monitor over to the server, but I don't want to if I don't have to.You really ought to. You'd have to go to a *lot* of trouble to mangle your system into letting go of all its file locks in /var (never mind putting everything back the way it was again when you were through). The best approach would be to boot off a CD & tinker with /var while your OS isn't running.

> **sarloth said:**
> I have since realized this was retarded at best.There are a few specialised situations when it's highly advisable (eg heavily loaded newsgroup/database servers), but for most configurations, you're right.

---

