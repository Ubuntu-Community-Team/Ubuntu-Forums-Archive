---
title: "Trying to install gadmin"
date: 2012-05-09
forum: Server Platforms
---

### Post by Spalmore on 2012-05-09
I am running Ubuntu 12.4 LTS and am trying to install gadmin tools to manage my squid and dhcp servers but the package depends on gadmin-dhcpd and this package has been removed from the repositories. What is the proper method for installing this. Do I have to enable the older repositories or is there something I am missing?

---

### Post by tkkaisla on 2012-05-14
I have same problem... Hope quick fix. gadmintools domain is parked.

---

### Post by Yakuza on 2012-08-12
It seems i'm not alone then...

EDIT: oh well I did this on 12.04 64bit (installed the Natty package)

```
sudo wget [http://launchpadlibrarian.net/59787485/gadmin-squid_0.1.3-2_amd64.deb](http://launchpadlibrarian.net/59787485/gadmin-squid_0.1.3-2_amd64.deb)
sudo apt-get install menu
sudo dpkg -i gadmin-squid_0.1.3-2_amd64.deb
```

Everything seems to work.

---

