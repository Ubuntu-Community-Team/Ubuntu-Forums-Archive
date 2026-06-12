---
title: "Trying to install php5-intl"
date: 2013-04-22
forum: Server Platforms
---

### Post by CheezItMan on 2013-04-22
Hello,

I'm trying to install php5-intl on my ubuntu 12.04 server.  However I'm getting:

> 
The following packages have unmet dependencies:
 php5-intl : Depends: libicu44 (>= 4.4.1-1) but it is not installable
E: Unable to correct problems, you have held broken packages.


I've also tried with pecl

> 
pecl install intl


But it asks me for the ICU Libraries and headers.  I'm uncertain where those would be.  I've tried the default and it gives me:

> ERROR: `/tmp/pear/temp/intl/configure --with-icu-dir=DEFAULT' failed

---

### Post by beboylips on 2013-04-23
Try 
```

apt-get update --fix-missing
apt-get upgrade -f

```

---

### Post by CheezItMan on 2013-04-23
Thanks for responding, that was the first thing I tried, although I gave it another go when I saw you posted this.  It didn't resolve the issue.

I'm sure another repository has [COLOR=#000000]*libicu44  *[/COLOR]Does anyone know a repo I can add to get it working?

> **beboylips said:**
> Try 
```

apt-get update --fix-missing
apt-get upgrade -f

```

---

### Post by CheezItMan on 2013-04-23
ok it seems in Ubuntu 12.04 libicu44 has been superseeded with llibicu48...

Now I need to figure out how to get a php & php-intl package that uses libicu48...

---

### Post by CheezItMan on 2013-04-23
Managed to get it working adding the:

ondrej-php5-precise

repository.  Now to figure out php5-apc...

---

