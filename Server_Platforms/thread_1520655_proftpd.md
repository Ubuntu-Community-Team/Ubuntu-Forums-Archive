---
title: "proftpd"
date: 2010-06-29
forum: Server Platforms
---

### Post by chippanfat on 2010-06-29
Hey all, 
Quick one for you

I have installed gadmin Proftpd using the command line,
```
aptitude install proftpd-mod-mysql
```

my aim is to have it working with an sql database.

anyway, I installed it using the terminal using that command.

I am also using the xubuntu desktop, and when I search around the menu the gui, it isn't installed.

although I can get to the configuration files but those could be from when I uninstalled it previously? ...

Any idea?
Cheers

---

### Post by windependence on 2010-06-30
Try:

```
apt-get install proftpd-mysql
```

To start it try /etc/init.d/proftpd start

BTW did you install MySQL first?

-Tim

---

### Post by chippanfat on 2010-06-30
hey,
that command did't work :/

this is what I had:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package proftpd-mysql is not available, but is referred to be another package
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package proftpd-mysql has no installation candidate
```

---

### Post by dapperdanny77 on 2010-07-02
I think you should do a 
>apt-get install proftpd-mod-mysql

---

