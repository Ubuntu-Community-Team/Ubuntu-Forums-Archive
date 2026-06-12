---
title: "Moving SSL Certificate to a new server"
date: 2007-04-07
forum: Server Platforms
---

### Post by yellowtip on 2007-04-07
Hi everybody,

I need to move an officially signed SSL certificate from an old Redhat7.3/Apache2 server to a spanking new Ubuntu 6.06 LAMP Server.

The new server also has a new IP address.

Can I simply move the certificate to the new server, or do I need to buy a new certificate?

If possible, I would also like to know which files I need to move.

Thanks in advance!

---

### Post by WesRatcliff on 2007-04-07
You'll need to move your signed cert, the server's private key the cert was generated with and and intermediary certs your signing authority may have used.

Open up your Apache SSL configuration, which by default is at/etc/httpd/conf.d/ssl.conf on RH 7.3 if I remember correctly, and you will see the filesystem location of your certs.

Wes Ratcliff

---

