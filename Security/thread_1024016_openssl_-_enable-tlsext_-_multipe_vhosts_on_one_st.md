---
title: "openssl - enable-tlsext - multipe vhosts on one static ip?"
date: 2008-12-28
forum: Security
---

### Post by kpm on 2008-12-28
After recovering from the price shock of a single ssl certificate from any of the few CA's out there, I was happy to learn of two methods that allowed one to purchase one certificate and have it apply to multiple virtual hosts. See:
[http://www.how2forge.org/enable-multiple-https-sites-on-one-ip-using-tls-extensions-on-debian-etch]("http://www.how2forge.org/enable-multiple-https-sites-on-one-ip-using-tls-extensions-on-debian-etch")
and
[http://www.g-loaded.eu/2007/08/10/ssl-enabled-name-based-apache-virtual-hosts-with-mod_gnutls/]("http://www.g-loaded.eu/2007/08/10/ssl-enabled-name-based-apache-virtual-hosts-with-mod_gnutls/")

I then learned after reading a forum post by Falko that:
[http://www.how2forge.org/forums/showthread.php?p=161829#post161829]("http://www.how2forge.org/forums/showthread.php?p=161829#post161829")
> ...mod_gnutls seems to be experimental and seems to cause high loads on the server...

So, I have opted to attempt this with Ubuntu 8.10.  Falco's tutorial is for Debian Etch, so I suppose it would be very similar on an Ubuntu distro, but I was wondering if anyone had any comments on this?  Or have successfully configured such a set up? Or if anyone knows if Ubuntu 8.10 actually supports the tls extension now?

Thanks

---

