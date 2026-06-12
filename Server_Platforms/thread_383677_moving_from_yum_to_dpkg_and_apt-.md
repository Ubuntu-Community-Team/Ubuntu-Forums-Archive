---
title: "moving from yum to dpkg and apt-*"
date: 2007-03-13
forum: Server Platforms
---

### Post by homli on 2007-03-13
On RHEL, I create a daily cron job that emails a list of available updates. For example:

```
vi /etc/cron.daily/yum_notify.cron
   #!/bin/bash
   /usr/bin/yum check-update 2>&1 | /bin/mail -s "yum notification" root
```

I don't see a dpkg or apt-* equivalent to 'yum check-update'. Am I missing it?

---

### Post by Nikron on 2007-03-13
Hmmm..   All I can think of is "apt-get update && apt-get -s upgrade"  Check for updates and return a simulation upgrade..

---

### Post by homli on 2007-03-13
> All I can think of is "apt-get update && apt-get -s upgrade"

'apt-get -s upgrade' is move verbose than 'yum check-update', but should do the job (and possibly provide additional useful information, such as the repo for each upgrade).

Thanks!

---

### Post by Brazen on 2007-03-13
> **homli said:**
> 'apt-get -s upgrade' is move verbose than 'yum check-update', but should do the job (and possibly provide additional useful information, such as the repo for each upgrade).

Thanks!

I believe cronapt can also be configured to email available updates.

[http://www.opal.dhs.org/programs/cron-apt/](http://www.opal.dhs.org/programs/cron-apt/)
[http://www.debian-administration.org/articles/162](http://www.debian-administration.org/articles/162)

---

