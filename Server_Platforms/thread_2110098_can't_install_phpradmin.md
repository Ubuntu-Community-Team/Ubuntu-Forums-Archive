---
title: "can't install phpradmin"
date: 2013-01-29
forum: Server Platforms
---

### Post by mike_sai on 2013-01-29
hi  :grin:, i am a newbie in ubuntu :sad:  and i have found i software named phpradmin, i have difficulties installing it ](*,),  the installation guide is only for fedora users, does someone know how  to install it in ubuntu (jaunty). any help will be welcome =D>, thank you



Thanks

---

### Post by codemaniac on 2013-01-29
Post moved to its own thread.

---

### Post by jonobr on 2013-01-29
Try running
> sudo apt-get update

then

> sudo apt-get upgrade

then

```
sudo apt-get install phpmyadmin
```

post errors you get 

thanks


jonobr

---

### Post by chrisguk on 2013-01-29
Something else to check.

Do you have a database client and server installed as well like mysql-server. If I recall PHPMyAdmin doesnt like it if they are not present.  Also Apache2 so that PHPMyAdmin can configure itself properly on install.

If you want a fresh canvas use these commands:

```
sudo apt-get --purge autoremove phpmyadmin
```

use that command for apache2 and any other package for that matter providing you havent spent time on custom configs etc.

The issue this:

```
apt-get update
```

```
apt-get install apache2 mysql-server mysql-client phpmyadmin
```

That should fix any previous config issues.

---

