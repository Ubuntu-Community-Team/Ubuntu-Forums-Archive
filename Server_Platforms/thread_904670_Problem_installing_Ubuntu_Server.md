---
title: "Problem installing Ubuntu Server"
date: 2008-08-29
forum: Server Platforms
---

### Post by XFactordx on 2008-08-29
Ubuntu server doesn't seem to want to install. I get to the CD prompt, hit install, and the server simply restarts and comes back to the prompt. Is there an issue? Thanks.

Tyan Thunder i7501 Pro (S2721-533)
Dual Xeon 2.8Ghz CPU Processors
2GB RAM
2x 160GB IDE Hard Drive

---

### Post by alastair on 2008-08-29
> **XFactordx said:**
> Ubuntu server doesn't seem to want to install. I get to the CD prompt, hit install, and the server simply restarts and comes back to the prompt. Is there an issue?

Before hitting "Install", try the F6 (additional args) option (IIRC).

You can append some extra params to the kernel after the "--".

Maybe try adding something like :

acpi=off

You could also remove the "splash" ansd "quiet" options - to see what might be output to screen before the problem.

But this is a guess - some machines are very quirky. Tyan may have a few like that ...

Alastair

---

### Post by XFactordx on 2008-09-02
Thanks for the advice.

Unfortunately this didn't work. I saw text running down the screen, but it suddenly stops and reboots the system. I don't see any error messages.

---

