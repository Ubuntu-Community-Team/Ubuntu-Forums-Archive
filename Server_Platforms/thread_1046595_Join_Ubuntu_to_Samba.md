---
title: "Join Ubuntu to Samba"
date: 2009-01-21
forum: Server Platforms
---

### Post by chispof on 2009-01-21
Hi, id already joined my desktop (ubuntu) to my samba server (centos), but my samba server works with ldap and when i reboot my ubuntu machine and try to log with a user from samba server, i cant log in. Please could any body help me?...


This server is already tested with Windows machines and it works perfectly.

---

### Post by chispof on 2009-01-21
sorry, this is my configurartion on /etc/samba/smb.conf

[global]
workgroup = example
security = domain
password server = 10.0.0.1

join rpc -D example -U administrator%password


and my /etc/nsswitch.conf

passwd:     compat ldap
group:      compat ldap

And that's all

---

