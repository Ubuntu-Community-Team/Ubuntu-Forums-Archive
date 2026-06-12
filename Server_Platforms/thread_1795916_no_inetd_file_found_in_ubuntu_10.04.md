---
title: "no inetd file found in ubuntu 10.04"
date: 2011-07-03
forum: Server Platforms
---

### Post by knils00717 on 2011-07-03
no inetd file found in ubuntu 10.04
after i run command sudo apt-get install openbsd inetd
still that file is not created : /etc/inetd.conf

---

### Post by SeijiSensei on 2011-07-03
Inetd has been deprecated for a long time now.  Use **xinetd** instead.

xinetd has a main configuration file, /etc/xinetd.conf, but the service-specific configurations are stored as individual files in /etc/xinetd.d.

---

### Post by knils00717 on 2011-07-03
> **SeijiSensei said:**
> Inetd has been deprecated for a long time now.  Use **xinetd** instead.

xinetd has a main configuration file, /etc/xinetd.conf, but the service-specific configurations are stored as individual files in /etc/xinetd.d.




.......................

Thanks for the reply>
But there is no such file like /etc/xinetd also:(

---

### Post by SeijiSensei on 2011-07-03
> **knils00717 said:**
> .......................

Thanks for the reply>
But there is no such file like /etc/xinetd also:(

Did you install it with "sudo apt-get install xinetd"?  It's not included by default on the workstation releases; I've forgotten whether it's included on the server version.

---

