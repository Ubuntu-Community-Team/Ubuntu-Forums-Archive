---
title: "Winbind seems does not work on 9.04"
date: 2009-05-23
forum: Server Platforms
---

### Post by visna on 2009-05-23
Hi guys,
I'm trying to configure winbind on ubuntu server 9.04, and i follow this link :
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

but when i try to join into 2003 domain it show me error: failed to find KDC service for domain mydomain.local

when i ping DNS (same as dc) server it works, but if i ping DNS server tih FQDN it fails.
Resolv.conf is ok, search mydomain.local and nameserver is my DNS server.

someone have trouble with winbind on new ubuntu server release?

thanks for any tips.
visna

---

### Post by kvizz on 2009-05-24
try to stop avahi-daemon - sudo /etc/init.d/avahi-daemon stop and ping your fqdn - had the same problem about a year ago with it because of .local, there is a bug on launchpad for this

---

### Post by visna on 2009-05-27
it works!

thanks very much kvizz.
But i need to set avahi-daemon disable?

---

### Post by kvizz on 2009-05-27
try to change /etc/nsswitch.conf from this "hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4" to this "hosts:files dns mdns4_minimal [NOTFOUND=return] mdns4"

---

