---
title: "snmpconf? where are thee..."
date: 2007-03-26
forum: Server Platforms
---

### Post by GumbyNoTalent on 2007-03-26
Pretty simple (6.10 Server, plain no LAMP or DNS);

apt-get install snmpd

and can't find snmpconf

Do I need to get another package?

---

### Post by Koybe on 2007-03-26
You can you the snmpconf command to get started with a configuration file.

---

### Post by WesRatcliff on 2007-03-26
Look here to find the package a file resides in: [http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file](http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file)

Alternatively you may edit /etc/snmpd.conf

Wes

---

### Post by crackmac on 2007-07-27
I think his point is it's missing... same here.

--Kevin Duane

Ubuntu Server
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty


> **GumbyNoTalent said:**
> Pretty simple (6.10 Server, plain no LAMP or DNS);

apt-get install snmpd

and can't find snmpconf

Do I need to get another package?

---

