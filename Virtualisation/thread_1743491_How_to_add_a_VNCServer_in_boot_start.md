---
title: "How to add a VNCServer in boot start?"
date: 2011-04-29
forum: Virtualisation
---

### Post by Fred2040 on 2011-04-29
Hi, I'm not sure if this question can be here...
But Anyway, it's about Remote Conexion, so... 

My SO is ubuntu x64 10.04 and I want to add a x11vnc server into reboot.
Then, I'm looking for a confortable way to get my pc's control, before it start.

And Well, Actually I'm using: GPG or encryptation... but, I don't see a way to use a VNC server from the begining, Anyway I have to ask..

How to add a VNCServer in boot start?

:KSMy apologizes if I talk like a caveman it's because: I don't speak english :)
And well, I appreciate your help

Best regards!

:P

---

### Post by krunge on 2011-04-29
To have x11vnc start at boot have a look here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
Follow the instructions in the "Continously" section. (You edit the display manager's startup script to start x11vnc.  If gdm is the display manager then /etc/gdm/Init/Default might be the startup script one adds an x11vnc cmdline to... see the above FAQ)

---

### Post by Fred2040 on 2011-05-05
Hey Thks a lot!

---

