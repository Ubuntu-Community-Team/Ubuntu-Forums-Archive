---
title: "LAMP reinstallation failed"
date: 2007-02-08
forum: Server Platforms
---

### Post by weekendli on 2007-02-08
After the LAMP remove from ubuntu, I mis-deleted all of there relative configuration files, /etc/apache2, php4, mysql, /etc/init.d/apache2, mysql.  However, on my second installation, apt-get install didn't install those configure files again.  Is it anything goes wrong? I don't want to reinstall the whole system again, anything would help. thanks. Or how can I make apt-get realize to install the configure files for me again?

---

### Post by weekendli on 2007-02-08
problem solved. I used synaptic packages manager to remove the lamp package completely. It's different from "apt-get remove/autoremove". It did remove all the configuration file.

---

