---
title: "Apache and Firestarter Autostart on BOOT"
date: 2007-07-17
forum: Server Platforms
---

### Post by ic3man on 2007-07-17
Hello i have a server and i want to run apache without having to login.
How can i do this?
Thanks

---

### Post by 505 on 2007-07-17
Just install Apache trough apt-get (or synaptic). It should set itself up to start as a service. Services are started before you log in. The file that is run is in /etc/init.d/

---

