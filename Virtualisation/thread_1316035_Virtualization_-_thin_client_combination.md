---
title: "Virtualization - thin client combination"
date: 2009-11-05
forum: Virtualisation
---

### Post by doyenne on 2009-11-05
I'm new to virtualization. Just some thoughts...

Would it be possible to do the following in a situation with +/- 8 workstations, in order to have every user have the same Windows XP installation and to minimize system administration time:

[LIST]
[*]Install a virtualization package on a server
[*]On the clients, start Linux (Ubuntu) which automatically connects to the server via the Linux Terminal Server Project, via X windows or another method
[*]For each connecting client, the server starts a Windows XP image
[*]This image is loaded into memory completely, so it is very fast
[*]Result: all users have the same Windows installation and work on thin clients, without the need for them to know this
[*]In this case, Windows Terminal Server should not be necessary
[/LIST]

*If* it is possible, is it possible with FOSS tools?

---

