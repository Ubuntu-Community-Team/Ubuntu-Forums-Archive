---
title: "Upgrade form Ubuntu 6.06 Server to Ubuntu 7.04 Desktop"
date: 2007-06-12
forum: Server Platforms
---

### Post by etechship on 2007-06-12
As you saw. If I have ubuntu 6.06 server installed on a computer, and I want to get 7.04 desktop on there, via upgrading it, what should I do?

another question: I have this computer set up with 3 monitors (2 PCI, 1 int.) and when-ever I try to load any ubuntu desktop edition, it takes a while, then it either loads strips or it's regular screen on the middle monitor. This computer has 1GB RAM so it shouldn't take so long, but ...

---

### Post by elst on 2007-06-12
Interesting question. I'd try doing the version upgrade first with update-manager, then rebooting, and finally adding the meta-package for your preferred desktop with apt-get (e.g. the "ubuntu-desktop" package for the default GNOME desktop).

I don't know anything at all about multi-monitor support, I'm afraid. This kind of thing is usually very dependent on the graphics card drivers, though. Somebody on the "Hardware and Laptops" forum might have an idea.

---

