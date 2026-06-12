---
title: "Sendmail TLS and self-signed certs"
date: 2015-03-05
forum: Server Platforms
---

### Post by ghughes on 2015-03-05
Good afternoon, all!

I'm working on setting up a sendmail server with TLS.  I've found some documents on setting up certs with a CA signed cert, but not much with self-signed certs.

The question is about the CACERT_PATH and CACERT lines in a standard sendmail config.  If I'm using self-signed certificates, it shouldn't make a difference what's in the CA lines - in fact, I shouldn't need them at all.

We have to use sendmail as the custom mailer we wrote for our application stack doesn't know Postfix.  

Any thoughts on this?

Thanks to all for considering this!

Gregg

---

### Post by ghughes on 2015-03-05
Never mind.  Yes, you do need them for TLS to start.  Just use the sl-cert-snakeoil.pem as the CACERT file.

---

