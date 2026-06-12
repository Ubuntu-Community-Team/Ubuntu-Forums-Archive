---
title: "How can I harden the securtity on my server (MySQL, Apache, VSFTPD, Drupal, etc...)"
date: 2007-04-18
forum: Server Platforms
---

### Post by SnowPunk98 on 2007-04-18
I setup Feisty server on a machine at home and so far have the following installed and either fully running or partially running. 

DansGuardian
MySQL
Apache
PHP5
VSFTPD
Drupal 5.1
SSH
ClamAV
Mondo
Squid
Samba

My question is I would like to harden all of these services to make them as secure as possible without crippling functionality. Public things are more important obviously, like Apahce, PHP, etc but if anyone wants to throw some guides or hints at me it would be appreciated.

---

### Post by jtc on 2007-04-18
> **SnowPunk98 said:**
> ...I would like to harden all of these services to make them as secure as possible without crippling functionality.

Actually, a big part in hardening a system is to cripple it. More precisly you ought to disable any functions and services you'r not using. The less you are running the lesser are the potential security holes.

---

