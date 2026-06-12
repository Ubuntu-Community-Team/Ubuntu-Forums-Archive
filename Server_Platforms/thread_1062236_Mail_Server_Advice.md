---
title: "Mail Server Advice"
date: 2009-02-06
forum: Server Platforms
---

### Post by faustcoder on 2009-02-06
I'm looking for information on creating a mail server that would be simple for other non Linux admins to manage. For instance we have a high user turnover rate. As a result we constantly have to add, remove and forward users mail. Also how would one go about storing backups or archives? We are required to keep email for 3 years, what would be the simplest way to do so. I plan on using Postfix, Dovecot (IMAP), MySQL (Virtual users/domains), Amavis, and possibly some webmail frontend.
Any information would be appreciated.

---

### Post by HermanAB on 2009-02-06
Citadel does it all.  It is very easy to install and comes with a web interface to manage it:
[http://citadel.org](http://citadel.org)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

Cheers,

Herman

---

### Post by jamesrfla on 2009-02-06
I would go with HermanAB advice. I use Citadel and it is very nice and if you have any questions installing or getting it working let us know.

---

### Post by faustcoder on 2009-02-06
Wow, awsome thank you. Thats exactly what I was looking for. I'll try it out and give you guys a heads up. Thanks!

---

### Post by faustcoder on 2009-02-10
I've gotten Citadel up and running. Works great. For those whom are curious setup is:
Ubuntu 8.10 running on VMware ESX.
8G disk, 2G Ram
Email is stored on a OpenFiler SAN using 4 500G hdd's raid10.

Citadel is perfect for those wanting a simple, full featured, groupware server.
Once again thanks guys for the info.

---

