---
title: "VirtualBox: Clock not synchronized after suspend"
date: 2008-12-17
forum: Virtualisation
---

### Post by csauer on 2008-12-17
Hello,

I have an installation of OpenSolaris 2008.11 running under VirtualBox on Ubuntu Intrepid. When I save the machine state in VirtualBox and restore it afterwards, everything works fine, except that the clock of the guest OS is set to the time it was suspended.

Would this be an OpenSolaris related bug or is there something i can do in VirtualBox?

Many thanks.

---

### Post by lonerook on 2009-06-17
Did you try to install the virtualbox "guest additions" in the guest system (OpenSolaris in this case). I had the same problem with by Ubuntu and Windows guest, but virtualbox guest additions contains a time synchronization tool.

---

