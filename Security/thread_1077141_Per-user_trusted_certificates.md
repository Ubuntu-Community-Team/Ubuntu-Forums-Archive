---
title: "Per-user trusted certificates?"
date: 2009-02-22
forum: Security
---

### Post by jniesz on 2009-02-22
Hi, I am wondering if there is a way to add trusted root/self-signed certificates just for my user, without adding them to /etc/ssl/certs.  I need them to be generally available (not just a Firefox exception) to applications that use OpenSSL, like Darcs, but at the same time I don't want to put them in the system-wide pool of certificates that other users will automatically trust too.  Is there a way to define another directory for OpenSSL to look in, something like a ~/.ssl/certs, that is an alternate set of trusted certificates?

---

