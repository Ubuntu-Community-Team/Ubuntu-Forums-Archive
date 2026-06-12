---
title: "Exim4 TLS error with PHP-CA certificates"
date: 2008-07-02
forum: Server Platforms
---

### Post by growse on 2008-07-02
I've had Exim4 running great for a while with the self-signed certs you can generate from the bundled script. However, I've just moved over to doing all my certificates with PHP-CA, the idea being that I have one CA that I trust, and use that to sign all my service's certificates.

The problem is that when I use the cert/key combination produced from PHP-CA, I get the following error when I try to start TLS through SMTP.

```

 TLS error on connection from ([IPv6:2001:770:xxxx:xxxx:xxxx]) [2001:770:xxxx:xxxx:xxxx] (cert/key setup: cert=/etc/ssl/certs/exim.crt key=/etc/ssl/private/exim.key): Error while reading file.

```

Files are readable by everyone, just in case it's a permissions issue. Anyone know what this fairly meaningless error means?

---

