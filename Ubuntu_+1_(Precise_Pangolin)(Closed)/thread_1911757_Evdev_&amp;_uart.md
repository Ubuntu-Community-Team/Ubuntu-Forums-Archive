---
title: "Evdev &amp; uart ?"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teh603 on 2012-01-19
So, I'm trying to diagnose and hopefully solve the problem of the eGalax touchscreen not working in Precise, when it worked in Ocelot. Far as I can tell, its an issue with the kernel image not being compiled to support EVDEV and UART input, and thus nothing related to the touchscreen is being properly handled. Needless to say, I keep getting a lot of responses of "Check the mainline kernel PPA" and no meaningful help.

Does anyone know how to check if the kernel supports those input modes, and enable them if they're not enabled by default?

---

### Post by dino99 on 2012-01-19
i'm not used with such config, but setting the good module(s) params then loading with dkms will avoid to recompile the kernel. The more difficult is to identify the module(s) :(

---

### Post by teh603 on 2012-01-19
Me either. That's why I'm asking for help.

For what its worth, the uep module should be loading to handle the touchscreen input, but modprobe can't find it.

---

