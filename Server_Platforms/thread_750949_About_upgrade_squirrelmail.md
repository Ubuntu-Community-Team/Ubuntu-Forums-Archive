---
title: "About upgrade squirrelmail"
date: 2008-04-10
forum: Server Platforms
---

### Post by satimis on 2008-04-10
Hi folks,


Ubuntu 7.04 server amd64
Squirrelmai 1.4.11


The package was downloaded on Squirrel website sometimes ago when it was not available on repo.  It is working w/o problem.

$ sudo find / -name squirrelmail```

/usr/local/squirrelmail
/var/local/squirrelmail
/etc/cron.daily/squirrelmail
/etc/squirrelmail

```


Now I found the package available on repo.

$ apt-cache policy squirrelmail```

squirrelmail:
  Installed: (none)
  Candidate: 2:1.4.9a-1ubuntu0.1
  Version table:
     2:1.4.9a-1ubuntu0.1 0
        500 http://security.ubuntu.com feisty-security/universe Packages
        100 /var/lib/dpkg/status
     2:1.4.9a-1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```
Please advise how to upgrade it to the lattest version?  TIA


B.R.
satimis

---

