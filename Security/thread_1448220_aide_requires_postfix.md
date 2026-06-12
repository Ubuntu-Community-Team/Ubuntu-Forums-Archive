---
title: "aide requires postfix?"
date: 2010-04-06
forum: Security
---

### Post by supremedalek on 2010-04-06
Why when I try to install aide, it wants to install postfix?

```
raub@test:~$ sudo apt-get install aide
apt-get: install aide
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aide-common bsd-mailx mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  aide aide-common bsd-mailx mailx postfix
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1469kB/2134kB of archives.
After this operation, 5579kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
raub@test:~$ 
```

I mean, all I should need is some kind of lightweight smtp thingie such as msmtp or even ssmtp if I all I am doing is sending out emails as opposite to a full blown mta, right?

---

### Post by cdenley on 2010-04-06
It appears to depend on postfix or anything providing mail-transport-agent. The package nullmailer should satisfy this dependency.
```

sudo apt-get install nullmailer aide

```

---

### Post by Bachstelze on 2010-04-06
As cenley said, it doesn't requite Postfix specifically, just any MTA. Since you didn't specify one, Apt defaults to Postfix.

---

