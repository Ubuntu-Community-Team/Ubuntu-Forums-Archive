---
title: "changing the default port on Openssl..."
date: 2007-11-01
forum: Server Platforms
---

### Post by Mia_tech on 2007-11-01
I have just installed OpenSSL on my kubuntu box, but I want to change the default port from 22 to lets say 5555.......

can anyone help

---

### Post by MJN on 2007-11-01
OpenSSH? Change the **port** directive in **/etc/ssh/sshd_config** and restart the service (**sudo /etc/init.d/ssh restart**).

Mathew

---

