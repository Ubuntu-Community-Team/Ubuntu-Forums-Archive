---
title: "CPU monitor for dual setups"
date: 2005-07-11
forum: Server Platforms
---

### Post by viniosity on 2005-07-11
Is there a CPU monitor application I can use to see how both my CPU's are working real-time?  I tried ascpu but it only shows one processor.  I'm monitoring this remotely so I'd need an X app that I can view using ssh -X as opposed to a gnome-applet or some such thing.

---

### Post by DJ_Max on 2005-07-11
[QUOTE=viniosity]Is there a CPU monitor application I can use to see how both my CPU's are working real-time?  I tried ascpu but it only shows one processor.  I'm monitoring this remotely so I'd need an X app that I can view using ssh -X as opposed to a gnome-applet or some such thing.[/QUOTE]
 Have you tried top? You don't need fancy X stuff for monitoring CPU usage.

---

### Post by viniosity on 2005-07-11
Using top I can see that when I'm doing intensive work (a database lookup that takes about 5 minutes) CPU1 is using 45% and CPU2 is around 2%.  Is that normal?  Shouldn't CPU2 be sharing the load a bit?

---

