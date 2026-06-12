---
title: "No to start X on logon"
date: 2009-03-24
forum: Server Platforms
---

### Post by Mauler5858 on 2009-03-24
I have Ubuntu Desktop 8.04 that I recently made headless and have it running as my home server.  I dont wish to remove the desktop components, but i do wish to stop it from booting into x on startup.  How do i go about doing this?

---

### Post by Mauler5858 on 2009-03-24
Disregard..solved with:

cd /etc/rc2.d
sudo mv S30gdm _S30gdm

---

