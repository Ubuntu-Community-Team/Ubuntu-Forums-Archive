---
title: "Which packages are kernel related in upgrade"
date: 2008-12-03
forum: Server Platforms
---

### Post by Joel Duckworth on 2008-12-03
Hi, I'm running Ubuntu Server Gutsy and I don't want to install the kernel updates with apt-get upgrade for various reasons. How can I know what packages are related to a kernel upgrade so I can exclude them from being installed? 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-server openssh-client openssh-server
The following packages will be upgraded:
  apt apt-utils bind9-host bzip2 cpio dnsutils krb5-user libbind9-30 libbz2-1.0 libcupsys2 libdbus-1-3
  libdns32 libgnutls13 libisc32 libisccc30 libisccfg30 libkadm55 libkrb53 liblwres30 libpcre3 libpq5 libssl0.9.8
  libxml2 linux-libc-dev linux-ubuntu-modules-2.6.22-14-server login logrotate passwd python-apt python2.5
  python2.5-minimal rsync samba samba-common tzdata update-manager-core winbind

Or perhaps there is an option in apt-get that I don't know about to block kernel installs? That would be nice.

---

### Post by cdtech on 2008-12-03
I know this is a lot to digest, but it's worth the read....
**2.2 The Debian package management system**
[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-kernel-details](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-kernel-details)

---

### Post by cariboo on 2008-12-03
To answer your question, just look athe the messages:

> he following packages have been kept back:
linux-image-server linux-server openssh-client openssh-server

If if your kernel gets updated, there is no need to reboot until you need to. My kernel was updated about a week ago, and I have no plans to rebbot in the next while, the server is on a ups so if there is a power bump, it will just keep running.

Jim

---

