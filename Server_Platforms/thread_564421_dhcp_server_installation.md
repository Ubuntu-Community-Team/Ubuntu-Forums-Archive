---
title: "dhcp server installation"
date: 2007-10-01
forum: Server Platforms
---

### Post by sadeeb on 2007-10-01
How do I configure my dhcp3-server?

---

### Post by Stormspace on 2007-10-01
I'd install webmin and do all my configuration from there. 

[Webmin Install]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty")

---

### Post by koenn on 2007-10-01
> **sadeeb said:**
> How do I configure my dhcp3-server?
the basics : [http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp)

---

### Post by ubnuturero on 2007-10-01
edit your  
  /etc/dhcp3/dhcp.conf   if  selfexplanatory

---

### Post by ubnuturero on 2007-10-01
I think webmin is not included  in ubuntu  for a  very good reason

---

### Post by ruibernardo on 2007-10-01
> **ubnuturero said:**
> I think webmin is not included  in ubuntu  for a  very good reason

Webmin isn't included in Ubuntu because it isn't maintained in Debian anymore. Webmin is upgraded every month (to much for  Debian/Ubuntu?) and some things break in Ubuntu. To be used with caution. For example, if you install packages with webmin and a question is asked by APT/dpkg, you can't respond to it and it starts with an endless loop.

Apart of this, I use it for many things (apache/mysql/etc) without problems.

It can be downloaded from its website (deb package). [Instructions here]("http://www.webmin.com/deb.html").

EDIT: I must confess that I've never used webmin to configure a DHCP server. :-k

---

### Post by Stormspace on 2007-10-01
I've configured two DHCP servers with Webmin and found it to be very stable and easy to do. And although I configured the first dhcp server manually, it was cool to see how my settings carried over to webmin and what other options were available that you might not know about without reading up on it alot. <deep breath>

---

