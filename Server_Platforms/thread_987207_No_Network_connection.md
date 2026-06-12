---
title: "No Network connection ?"
date: 2008-11-19
forum: Server Platforms
---

### Post by Kari_Juhani on 2008-11-19
Hello all...

i installe Proftpd and Webmin to my 8.10 Server... now FTP and other services work, but i cant update via apt-get. I get error that says "Could not resolve 'fi.archive.ubuntu.com'

i can ping some IP's,mainly in same router.

Is there some option that i should enable from Webmin, or is this just some missed setting ???

Kari

---

### Post by Wayne_V on 2008-11-19
Sounds like a default route issue.  What does "$ route -n" say?

For fi.archive.ubuntu.com I get:

$ nslookup  fi.archive.ubuntu.com
fi.archive.ubuntu.com    canonical name = mirrors.nic.funet.fi.
Name:    mirrors.nic.funet.fi
Address: 193.166.3.5

Try "$ sudo traceroute -n 193.166.3.5"

Send "$ cat /etc/resolv.conf" and "$ cat /etc/network/interfaces"

---

