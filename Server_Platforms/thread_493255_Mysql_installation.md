---
title: "Mysql installation"
date: 2007-07-05
forum: Server Platforms
---

### Post by wolfvilleian on 2007-07-05
Hi, I installed mysql and didn't configure it right and removed it and installed it again with apt-get, however it still kept the config file. So I deleted it and went to install it again but it didn't create a new one, I think apt-get still thinks the configs are still there when they aren't. How can I fix this?

Thanks in advance.

---

### Post by capitalistpiglet on 2007-07-05
Try purging the configuration files with apt-get --purge remove then reinstall mysql.

---

