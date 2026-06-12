---
title: "/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_intrepid-security_main_source_Sou"
date: 2008-11-02
forum: Server Platforms
---

### Post by Windows_ on 2008-11-02
Hi, all! 

I've installed ubuntu server **8.10**. 
But when I try 

**#apt-get build-deb php5**

the error is occur - 

**Can't open file: /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_intrepid-security_main_source_Sources**

What can I do to appear this file?

---

### Post by Windows_ on 2008-11-04
This problem was solved by
# apt-get update

:)

---

