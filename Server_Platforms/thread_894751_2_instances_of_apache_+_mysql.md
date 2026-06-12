---
title: "2 instances of apache + mysql"
date: 2008-08-19
forum: Server Platforms
---

### Post by deafpanda on 2008-08-19
Hi all,

I've got XAMPP for linux running on hardy.  I've also got apache and mysql installed separately, and these run whenever I turn on my computer.  I don't want them to run at all, I want XAMPP to run every time I turn on my computer.

Sorry if this question is really simple.

Help much appreciated :)

---

### Post by Ximbiot on 2008-08-19
Assuming XAMPP really isn't dependent on apache2 and mysql, why not just uninstall them?

```
apt-get remove apache2-common mysql-server
```

If this is not an option for some reason, you can use `update-rc.d' to prevent them from starting.  This would look something like this for Apache:

```
update-rc.d apache2 stop 09 0 1 2 3 4 5 6 .
```

---

### Post by deafpanda on 2008-08-20
Thanks, there were about 7 apache packages listed and I wasn't sure whether some were from XAMPP.  Solved now, thanks.

---

