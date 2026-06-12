---
title: "chowned the whole server install by mistake, need help...."
date: 2014-07-05
forum: Server Platforms
---

### Post by Heeter on 2014-07-05
Hi all,

I was working on my webserver (Ubuntu14.10), when I entered this code by mistake
```

chown -R -v -f www-data:www-data /*

```

I was actually meaning to enter
```

chown -R -v -f www-data:www-data /var/www/html/*

```

What can I do to revert my mistake?

Please, any assistance will be greatly appreciated..

Heeter

---

### Post by ian-weisser on 2014-07-05
There is no way to revert the command.
The command line shell predates the concept of 'undo'
It's permanent.

You have three options:

1) chown each directory and subdirectory and file in the system back to the correct owner
    This is the slowest, most tedious, and most error-prone option.

2) restore from backup (You *do *have a backup? You should! Stuff happens.)
    This is fastest and easiest.

3) reinstall
    This is still much faster than fixing thousands of directories and files manually.

---

### Post by Heeter on 2014-07-06
Kinda figured, Thanks for the reponse


Heeter

---

### Post by CharlesA on 2014-07-06
Did you run that command as root or as your user?

---

### Post by Heeter on 2014-07-06
As root


Heeter

---

### Post by CharlesA on 2014-07-06
Yep, pretty much boned. You could backup your config files and the package list and reinstall or restore from backups.

---

### Post by Heeter on 2014-07-06
backups, here I come..........................

---

