---
title: "Slapd doenot work perfectly"
date: 2011-01-27
forum: Server Platforms
---

### Post by Anandhkumar on 2011-01-27
Hi everyone,

I am using ubuntu server 10.10 for deploying my web application. I use openldap version 2.4.23 to authenticate the users for that web application. 

But for the first time when i configure the openldap it works perfectly and i am able to bind the "userPassword" attribute. But when i either restart the openldap service or reboot the system i couldnot bind the same attribute again. I'm getting "Invalid credentials,LDAP error code-49" error.But at any point of time i could able to bind the rootDN.

I tried installing,configuring and restarting the openldap server with both "root" privileges and with also "least user" privileges. But the problem still exists.

I am using the same "slapd.conf" and the schema files which i was using for the openldap 2.4.15 in ubuntu 9.04 desktop edition.

Is there anything different has to be done for ubuntu 10.10 than in ubuntu 9.04.

Any help would be greatly appreciated.

Thanks

---

