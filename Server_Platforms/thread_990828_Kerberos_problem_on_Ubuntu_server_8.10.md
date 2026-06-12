---
title: "Kerberos problem on Ubuntu server 8.10"
date: 2008-11-23
forum: Server Platforms
---

### Post by efagerho on 2008-11-23
Hi,

I have a problem with the hostnames. If I try to ssh into my box from an OpenBSD or FreeBSD box, then no password is asked. However, if I'm on the Ubuntu server and try to ssh to itself with its hostname, then I'm asked for a password and see the following in the logs of the KDC:

2008-11-23T11:22:52 TGS-REQ [email]efagerho@REALM.NET[/email] from IPv4:192.168.0.10 for host/ubuntu@REALM.NET [canonicalize]
2008-11-23T11:22:52 Server not found in database: host/ubuntu@REALM.NET: No such entry in the database

The problem is that it uses the hostname instead of the FQDN. If I try to SSH to itself with the FQDN, then everything works as it should. What should I do on the Ubuntu box to get it to automatically append the domain to the hostname when asking for service tickets?

Thanks.

---

