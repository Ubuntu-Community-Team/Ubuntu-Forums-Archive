---
title: "Ubuntu Server on Cray's CX1 Supercomputer"
date: 2008-10-22
forum: Server Platforms
---

### Post by eurohim on 2008-10-22
Would it work?

---

### Post by lykwydchykyn on 2008-10-22
Send me one, I'll let you know...

CX1 is using Xeon processors, so unless there's some special sauce component in there, I would think it'd work.  Maybe you'd have to recompile the kernel to take advantage of that many cpus and that amount of RAM.

I am fairly certain Ubuntu Server is not optimized for a machine like that, in any case.

---

### Post by cariboo on 2008-10-22
If your Cray has an OS you could probably run quite a few instances of linux virtually.

If I remember correctly IBM had a Mainframe that ran over a 1000 virtual instances of linux at one time.

Jim

---

### Post by EmmEff on 2008-10-23
> **eurohim said:**
> Would it work?

Should work fine.  It's regular Intel hardware.  It will run RH 5.2 and Windows CCE, among others.

---

