---
title: "shutdown comand"
date: 2007-04-09
forum: Server Platforms
---

### Post by jmvidalvia on 2007-04-09
Hello!
Just a simple question:
which is the right command to close a server?
I know there are shutdown and halt, with many options, but never know which is the best  one.
Thanks again!

---

### Post by rufius on 2007-04-09
The pretty standard system shutdown is "shutdown -h now". Now the command 'halt' is not always the same on different *nix's. In some it can be bad to call a halt, it being a last ditch effort to shutdown.

---

### Post by MJN on 2007-04-09
Probably better to use **shutdown -h_P_ now** as on some systems a bare -h won't actually turn the machine completely off (which is probably the intention).

Mathew

---

### Post by jmvidalvia on 2007-04-09
Thanks to both!
No more unpluggin my server...
;)

---

### Post by rufius on 2007-04-09
> **MJN said:**
> Probably better to use **shutdown -h_P_ now** as on some systems a bare -h won't actually turn the machine completely off (which is probably the intention).

Mathew

A good point, I forgot about that ;). Kind of like my Sun e220r server, it stays on unless you use the -P switch.

---

