---
title: "Upgrade not all done?"
date: 2008-10-28
forum: Server Platforms
---

### Post by Vegan on 2008-10-28
sudo apt-get upgrade

The following packages have been kept back:
  bind9 bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30 linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.


Thoughts

---

### Post by MJN on 2008-10-28
It is likely because the upgrading of those packages requires the installation of some packages not currently installed. The standard 'upgrade' will not do so if new packages are required.

In order to upgrade these packages, run **sudo apt-get dist-upgrade** - this will install whatever packages are required to proceed.

See the apt-get man page for further details.

Mathew

---

### Post by DanneUK on 2008-12-13
> The following packages have been kept back:
bind9 bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30 linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.


I had the same message come up after an apt-get upgrade

I found the solution by typing ```
aptitude why-not linux-server
```

The answer was: this packge must be installed manually

So just type in ```
apt-get install bind9 bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30 linux-image-server linux-server
```

and it will install these packages.  Reboot after.

---

### Post by MJN on 2008-12-14
Did the 'dist-upgrade' option not work for you?

Mathew

---

### Post by DanneUK on 2008-12-15
Didn't try the dist-upgrade option.  I read this thread after I had solved it.  The "aptitude why-not" just said 'manual install required'

---

### Post by MJN on 2008-12-15
The reason for that is that the 'install' option will also install any necessary dependencies, whereas the standard 'upgrade' option will not (only 'dist-upgrade' will).

Mathew

---

