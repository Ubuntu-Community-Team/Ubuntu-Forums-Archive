---
title: "ldap Berkeley DB recover after crash"
date: 2006-05-18
forum: Server Platforms
---

### Post by rsmereka on 2006-05-18
Hi All,

I have a Ubuntu 5.10 machine with Openldap and the Berkeley DB backend. I am managing the data with phpldapadmin along with apache2. Everything was working fine. This morning, I discovered that this machine rebooted sometime during the nite. Now all the data that I added using phpldapadmin is gone (the entire 'ou') and I have a couple of questions.

Firstly, how do I recover the database back to where it was before the outage? Second, what causes the data to disappear like that? Are the transactions not being commited? When I am managing using phpldapadmin, are there some settings in Berkeley DB that I should activate to make sure that the data is commited?

Any/all help is greatly appreciated,
Rick

---

### Post by rsmereka on 2006-05-18
An update,

After doing more research, I believe that I need the tool > db_recover to recover the database back to what is was. Unfortunately, this tool is not present on the server in question and I have to go and find which package it is in.

---

