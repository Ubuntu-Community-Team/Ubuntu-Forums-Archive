---
title: "Reverting Edgy server to PHP4"
date: 2006-11-29
forum: Server Platforms
---

### Post by DigitalGunfire.com on 2006-11-29
Hi all,

I recently installed the latest version of Ubuntu server on a box here, and I selected the LAMP option. It automatically installed PHP5, and I need to use PHP4 (for CLI and web.)

What is the cleanest way to revert to PHP4 from PHP5 in Ubuntu?

Thanks for any help you can provide.

---

### Post by loell on 2006-11-29
i think you can remove php5 by doing

```
sudo aptitude remove php5 php5-mysql libapache2-mod-php5 
```

and install php4

by

```
sudo aptitude install php4 libapache2-mod-php4 libapache2-mod-auth-mysql  php4-mysql
```

---

