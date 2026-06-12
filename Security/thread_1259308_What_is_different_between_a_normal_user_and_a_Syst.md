---
title: "What is different between a normal user and a System user?"
date: 2009-09-06
forum: Security
---

### Post by legolas_w on 2009-09-06
Hi
I saw that useradd command can create user which are from system type (using -r or --system). What is different between this user and user created without this parameter?

Thanks.

---

### Post by bodhi.zazen on 2009-09-06
A system user is in the admin group and can access root via sudo

A regular user has no root access.

---

### Post by Bachstelze on 2009-09-06
> **bodhi.zazen said:**
> A system user is in the admin group and can access root via sudo

A regular user has no root access.

Wrong. A system user account is an account that is not meant to be used by a human user, but by the system to run various system programs, usually daemons. Examples of such users include www-data, mysql, bind, ntpd, etc..

---

