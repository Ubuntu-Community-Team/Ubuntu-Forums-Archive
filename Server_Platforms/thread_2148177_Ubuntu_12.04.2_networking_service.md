---
title: "Ubuntu 12.04.2 networking service"
date: 2013-05-24
forum: Server Platforms
---

### Post by jcputter on 2013-05-24
sudo service networking restart

stop: Unknown instance:
networking stop/waiting

what is the most correct method to restart the networking services? /etc/init.d/networking restart was the old method right?

---

### Post by brent1975 on 2013-05-24
sudo /etc/init.d/networking restart

---

### Post by shekhar singh tomar on 2013-06-11
whenver I do service networking rsetart in Ubuntu 13.04.My system gets hang and every application is closed and I have to do a hard system reboot.

---

