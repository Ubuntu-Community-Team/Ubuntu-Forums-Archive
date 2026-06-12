---
title: "Installing Apache2 module proxy_ajp"
date: 2006-07-22
forum: Server Platforms
---

### Post by mikkel_j on 2006-07-22
Just installed the LAMP server for Dapper Drake and I am very pleased with the mechanism for enabling modules.

Unfortunately I need mod_proxy_ajp which is not among the available :-(

Neither can I find it using "apt-cache search" so can someone provide a hint as to how I install it???

---

### Post by mlind on 2006-07-22
> **mikkel_j said:**
> Just installed the LAMP server for Dapper Drake and I am very pleased with the mechanism for enabling modules.

Unfortunately I need mod_proxy_ajp which is not among the available :-(

Neither can I find it using "apt-cache search" so can someone provide a hint as to how I install it???

This is probably different than mod_jk (libapache2-mod-jk) ..

I couldn't find this module from APT repositories, but enabling/disabling apache2 modules you use **a2enmod** and **a2dismod**.

---

### Post by mikkel_j on 2006-07-23
It seems that the Apache version included in Dapper Drake is 2.0.55    
while mod_proxy_ajp is only compatible with 2.1 and later.

Is there an easy way to get the latest Apache 2.2.2 installed (like   
apt-get) or do I have to build from source?

---

### Post by mlind on 2006-07-23
Even edgy doesn't have newer apache2 than 2.0.55. I guess you'll have to build it from source yourself.

---

