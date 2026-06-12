---
title: "pure-ftpd"
date: 2007-01-16
forum: Server Platforms
---

### Post by ew16301 on 2007-01-16
Im confused about pure-ftpd. Im running Ubuntu 6.10 and installed pure-ftpd using apt-get. It started fine, and I can connect fine. But I cant change any options. It says "Cant start server in standalone mode: address already in use". It gives me this when trying to change anything...like max users. Any ideas?

---

### Post by discord on 2007-01-17
sounds like its trying to use an already in use ip adress. Find the documentation /usr/share/doc/proftpsomething  and look how to set it up...

---

### Post by PetePete on 2007-01-17
are you restarting the server , or just starting it when you change a setting in the config file? make sure to stop it then start it... cd /etc/init.d  then ./proftp restart

---

