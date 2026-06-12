---
title: "cacti server; free memory slowly drops toward 0"
date: 2007-09-21
forum: Server Platforms
---

### Post by Sgurd on 2007-09-21
I'm an intermediate user.  I have an ubuntu server running cacti and nothing else.  

It works great and didn't have any issues for the first couple days.  Now I'm seeing my free memory drop and drop towards 0.

Here's the graph.

[IMG]http://img222.imageshack.us/img222/3756/graphimagephpuq5.png[/IMG]

Can someone tell me what's going on?  Is my free memory really shrinking?

Perhaps I should schedule some nightly reboots?

   Thanks - JD

---

### Post by steve.horsley on 2007-09-23
It doesn't have to be a problem. I believe that Linux uses free memory as disk cache if it has no other use for it. Makes sense, really. If another app needs the memory then some of that disk cache gets reallocateed.

---

### Post by Sgurd on 2007-09-23
> **steve.horsley said:**
> It doesn't have to be a problem. I believe that Linux uses free memory as disk cache if it has no other use for it. Makes sense, really. If another app needs the memory then some of that disk cache gets reallocateed.

Cool.  I'll just let it keep on running them.  Thanks for the reply.

---

### Post by wirelessmonkey on 2007-09-23
You can also run 'top' or 'htop' from the command line and see what, if anything, is actively using memory.

---

