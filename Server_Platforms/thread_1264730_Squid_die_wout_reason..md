---
title: "Squid die w/out reason."
date: 2009-09-12
forum: Server Platforms
---

### Post by braiamp on 2009-09-12
I get an a windows to post this threat to get help about squid. I have a Ubuntu Server with a chain proxy using DG & Squid3 to use ClamAV and in some case squid simply die w/out log, no reason. If I execute sudo /etc/init.d/squid3 start && sudo /etc/init.d/squid3 start && sudo /etc/init.d/squid3 start && sudo /etc/init.d/squid3 start; about a thousand i get for 5 fails and two OK. This is so strange. I use a own build squid using apt-build and a normal optimization.  thanks.

---

### Post by braiamp on 2009-09-12
It´s a bug of the apt-build package. I purge squid and reinstall it from the repositories and it work.

---

