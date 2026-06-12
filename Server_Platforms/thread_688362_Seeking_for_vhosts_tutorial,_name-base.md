---
title: "Seeking for vhosts tutorial, name-base"
date: 2008-02-05
forum: Server Platforms
---

### Post by satimis on 2008-02-05
Hi folks,


VMWare Server
Bridged connection


Ubuntu 7.04 server amd64 (Host)
Apache/2.2.3
LAN IP 192.168.0.10


CentOS 5 x86_64 (Guest)
Apache
LAN IP 192.168.0.20


Router
All www ports, 80, 443 and 8080 are connected to Ubuntu
No port forwarded to CentOS


Domain
domain1.com - pointing to Ubuntu
domain2.com - pointing to CentOS



Can any folk advise me where can I find a tutorial to setup vhosts, name-base, on Ubuntu?  Google search brought me;

[http://gentoo-wiki.com/HOWTO_Apache_VirtualHost_by_IP_Address](http://gentoo-wiki.com/HOWTO_Apache_VirtualHost_by_IP_Address)

which, I think, can be modified for my use.  But I can't find /etc/apache2/conf/vhosts/vhosts.conf.  Whether I have to create it together with the directories above /conf/vhosts/vhosts.conf.  OR their file structure is different to Ubuntu.  Advice would be appreciated.  TIA



B.R.
satimis

---

### Post by kirsche on 2008-02-06
have a look here:
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

I use 3 virtual hosts (FQDN based) on an Apache2 here - works just fine.

---

