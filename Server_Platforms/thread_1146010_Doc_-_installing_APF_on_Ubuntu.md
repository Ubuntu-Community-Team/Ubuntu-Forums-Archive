---
title: "Doc - installing APF on Ubuntu"
date: 2009-05-02
forum: Server Platforms
---

### Post by satimis on 2009-05-02
Hi folks,

Ubuntu 8.04-i386-minimal
guest - OpenVZ
Mail server


Has any folk tried APF?
APF Firewall for Ubuntu and ArchLinux:
[http://codeblog.palos.ro/2008/02/28/apf-firewall-patches/](http://codeblog.palos.ro/2008/02/28/apf-firewall-patches/)


It is on repo;
# apt-cache search apf | grep apf```

apf-client - Client for Active Port Forwarding
apf-server - Server for Active Port Forwarding
dphys-swapfile - Autogenerate and use a swap file
imapfilter - filter mail in your IMAP account
snmptrapfmt - A configurable snmp trap handler daemon for snmpd

```

Where can I find relevant doc for config it on Ubuntu?  Do I need installing both apf-client and apf-server?

I can't run Shorewall and Iptables here because of running OpenVZ kernel.

# uname -r```

2.6.24-23-openvz

```

Please advise.  Pointer would be appreciate.  TIA

B.R.
satimis

---

