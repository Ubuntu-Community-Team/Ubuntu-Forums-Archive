---
title: "postgres configuration files"
date: 2007-05-26
forum: Repositories &amp; Backports
---

### Post by yee379 on 2007-05-26
i apt-get removed postgres all all dependent debs. i then manually deleted all configs etc from my system (/etc/postgres, /etc/postgres-common, /var/lib/postgres etc) from my system (6.10).

however, i want to reinstall postgres now; however, none of the configuration files nor the database directory is regenerated upon the apt-get install postgresql command. any ideas how i could get the configs etc back up? ie what deb/package do i need to reinstall or what command can i run to put all the default configuration files back onto my ubuntu?

cheers,

---

### Post by selfeky on 2007-12-04
I have the exact problem!
did you manage to fix it?

---

### Post by mlind on 2007-12-07
> **selfeky said:**
> I have the exact problem!
did you manage to fix it?

Easiest way is to probably purge your postgresql package (e.g postgresql-8.2) and the reinstall it back. Removing instead of purging a package doesn't remove its configuration files (like files in /etc).

If you have postgresql-8.2 installed (otherwise replace the purged/installed package)
```

sudo aptitude purge --purge-unused postgresql-8.2
sudo aptitude install postgresql-8.2

```

Purge may remove the database files from /var/lib/postgresql/, so if you need those - make a backup first.

---

