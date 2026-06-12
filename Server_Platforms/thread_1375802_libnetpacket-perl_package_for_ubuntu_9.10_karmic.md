---
title: "libnetpacket-perl package for ubuntu 9.10 karmic"
date: 2010-01-08
forum: Server Platforms
---

### Post by jeffk on 2010-01-08
I need to install the following dependencies for [synspam]("http://www.synspam.org") on Ubuntu 9.10 karmic server:

```
sudo aptitude install nfqueue-bindings-perl libsys-syslog-perl libappconfig-perl libnetpacket-perl libnetaddr-ip-perl
dpkg -i synspam_version_all.deb
```

Of these, only libnetpacket-perl is not packaged for Ubuntu 9.10 karmic.

Is this functionality present in another 9.10 package with a different name?

10.04 Lucid does have the package:

[http://packages.ubuntu.com/lucid/libnetpacket-perl](http://packages.ubuntu.com/lucid/libnetpacket-perl)

Can this be obtained via a backport of some kind?

Thanks.

---

### Post by Agone on 2010-08-18
[http://packages.debian.org/fr/sid/libnetpacket-perl](http://packages.debian.org/fr/sid/libnetpacket-perl)

---

