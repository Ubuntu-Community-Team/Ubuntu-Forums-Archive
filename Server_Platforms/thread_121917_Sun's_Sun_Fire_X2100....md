---
title: "Sun's Sun Fire X2100..."
date: 2006-01-26
forum: Server Platforms
---

### Post by oberon on 2006-01-26
Has anyone had any experiance running/installing Ubuntu on this hardware.  I am looking into purchasing a few for an upcoming project.

Thanks,

oberon

---

### Post by drogoh on 2006-01-26
Edit:

I should probably go to sleep.  I forgot Sun sells non-SPARC hardware. :)

---

### Post by Glut on 2006-01-26
Yep, we run a couple at the moment in a test lab. The only issue thus far is the known problem with AMD 64 dual-cores changing cpu frequency changing the clock rate not being handled correctly by the kernel. There are work arounds that are fine (running the cpu @ max frequency all the time) I'm not sure if the ubuntu kernel package includes the actual fixes, though. This is not an issue on the single core versions. 

Besides that, no problems thus far. We're almost finished testing on the first server, it should become production in the next 2 weeks. I'm quite happy with them.

---

### Post by oberon on 2006-01-27
Thats just what I wanted to hear!! \\:D/

Thanks,
oberon

---

