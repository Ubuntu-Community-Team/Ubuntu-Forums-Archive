---
title: "LTSP - Question"
date: 2010-01-21
forum: Server Platforms
---

### Post by Fede-CZ on 2010-01-21
Hi everybody,

            I'm wondering if someone could teach me the way to make an LTSP server (Ubuntu Server based) that makes my thin-clients boot a different OS/Ditribution than the one the server uses, I want them to use a full-desktop enviroment (Custom one) while the server is running under an Ubuntu Server based OS (What means : no GUI, no APPs, no Desktop, etc.)

Thank you very much.

---

### Post by steven.jones on 2010-01-21
Virtualise the OSes you want on ubuntu and connect to them...via the thin client. You could download the thin OS via tftp....but its simple....so you need resources.

Im not aware of any other way...in which case if the underlying server has no other function downloading the free VMware ESXi and running OSes in that would probably be easier.

---

### Post by Fede-CZ on 2010-01-22
I'm not getting the point :-? Don't I need to create an image of the OS (Which actually is Ubuntu) that I want my thin-clients use, and save it to an specific directory on my server?

---

