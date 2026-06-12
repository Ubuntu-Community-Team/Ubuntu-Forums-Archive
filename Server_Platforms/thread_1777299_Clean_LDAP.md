---
title: "Clean LDAP"
date: 2011-06-07
forum: Server Platforms
---

### Post by shawn.abdushakur on 2011-06-07
Hi, 

Does anyone know how to do a clean LDAP install after having thoroughly messed up a previous one? Basically, I'd like to completely remove ldap, configs, etc. and do a clean install.

Thanks in advance.

Shawn

---

### Post by ZuOverture on 2011-06-08
What kind of LDAP do you mean?

---

### Post by shawn.abdushakur on 2011-06-08
openLDAP, slapd.

---

### Post by blind2314 on 2011-06-08
> **shawn.abdushakur said:**
> openLDAP, slapd.
 
I believe that open-LDAP has the same properties as Sun LDAP; that is, a re-install will do a "clean" install. To that end, save any configs you want to keep before hand, if there are any.

---

### Post by shawn.abdushakur on 2011-06-08
I've tried apt-get purge as I don't want any configs saved or anything related to openldap for that matter. This is my first time trying to set it up. The problem I'm running into is when I apt-get purge slapd, I try to setup again and when I try to ldapadd something, it asks for authentication, but I haven't set a password anywhere or if I have, I don't know where or who the password is for. The only password is in the file that I'm trying to ldapadd. Thanks again.

---

### Post by shgn on 2011-06-19
i think your problem is in your configurations.
at first, at least, you should set the admin password in cn=config.

if it is wrong, please tell me the right one.
TNX

---

### Post by wdschei on 2011-09-13
Did you ever get a resolution to this?

I am following the replication tutorial and want to make sure my notes are correct, but even after a purge the old database is still hanging around.

---

### Post by shawn.abdushakur on 2011-09-14
unfortunatley i never did. i had the same problem along with some others i encountered with unbuntu server. that and some other factors prompted me to switch to centos where i successfully setup ldap.

---

