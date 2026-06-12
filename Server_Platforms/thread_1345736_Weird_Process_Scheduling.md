---
title: "Weird Process Scheduling"
date: 2009-12-04
forum: Server Platforms
---

### Post by karlson on 2009-12-04
I am running into a weird CPU scheduling bug with Jaunty.

When a user starts a computational process it runs fine taking CPU as it is needed.

When the same process is started by the same user a second time the 2 processes share CPU.  I have not tried checking what will happen when 3rd or 4th instances are started, but for 2 processes we find it a fairly consistent behavior.

I can change this by using taskset, but this has it's own dangers.  

Has anyone seen this?  Has anyone been able to fix this?

This was not the behavior in Intrepid.

---

### Post by karlson on 2009-12-07
Bump?

---

