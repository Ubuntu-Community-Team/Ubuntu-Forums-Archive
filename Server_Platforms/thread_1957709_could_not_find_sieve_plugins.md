---
title: "could not find sieve plugins"
date: 2012-04-13
forum: Server Platforms
---

### Post by ali888 on 2012-04-13
Hi, 

I wonder if someone can help me out. I run a machine running on Ubuntu Server 10.04 with postfix, dovecot 1.2.9, ldap and squirrelmail. I was trying to install sieve so that I can add a vacation option on the squirrelmail. I have installed avelsieve for squirrelmail from the synaptic package manager, but I could not find sieve.

So I went to download dovecot-1.2-sieve-0.1.19 from dovecot LDA website. However, I am stuck when trying to run
```
 ./configure --with-dovecot=path
``` 
as I am still getting used to the linux system. 

My dovecot config file sits in /etc/dovecot. So when I run that ./configure command, I received error message saying configure: error: dovecot-config not found. Of course, it could not find the dovecot-config in /etc/dovecot because the config file is named dovecot.conf. So I am very confused as what to do.

Any help would be appreciated. Thank you

---

