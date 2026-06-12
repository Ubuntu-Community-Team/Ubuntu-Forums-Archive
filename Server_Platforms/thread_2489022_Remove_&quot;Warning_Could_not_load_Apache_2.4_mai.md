---
title: "Remove &quot;Warning: Could not load Apache 2.4 maintainer script helper.&quot; error"
date: 2023-07-15
forum: Server Platforms
---

### Post by Heeter on 2023-07-15
Hey all,

Running Ubuntu20LTS/Nginx/PHP8.2

I found apache installed on this webserver, (Don't know How, Never used it, never intentionally installed it either, but that is another matter....)

I uninstalled it:
```

sudo apt-get remove --purge apache2 apache2-utils
sudo rm -rf /etc/apache2

```


Now I am getting this when I run the "apt upgrade"

```

Warning: Could not load Apache 2.4 maintainer script helper.

```

Can't seem to find where this is hiding

Got no php modules with apache listed

How can I get rid of this?

Regards

---

### Post by Xian on 2023-07-17
$ sudo apt-get install --dry-run php8.2
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  [COLOR=#ff0000]apache2 apache2-bin apache2-data apache2-utils [/COLOR]libapache2-mod-php8.2 libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap liblua5.3-0 php-common
  php8.2-cli php8.2-common php8.2-opcache php8.2-readline

---

### Post by Heeter on 2023-07-18
Great Thank you for this

Regards

---

