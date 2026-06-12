---
title: "Unable to load dynamic library '/usr/lib/php4/20050606/gd.so ..."
date: 2006-04-22
forum: Server Platforms
---

### Post by sYs^ on 2006-04-22
Hi,

I'd like to enable GD support on my server, I use *Apache/2.0.55 (Debian) PHP/4.4.2-1+b1 mod_ssl/2.0.55 OpenSSL/0.9.8a* (sorry for posting a debian problem here, but it's very similar and perhaps you can help too). I have gd extension enabled in my php.ini but when I restart my apache it writes this to the error.log:

```
[Sat Apr 22 18:24:09 2006] [notice] SIGHUP received.  Attempting to restart
PHP Warning:  mime_magic: type regex\t\tBEGIN[[:space:]]*[{]\tapplication/x-awk invalid in Unknown on line 0
**PHP Warning:  Unknown(): Unable to load dynamic library '/usr/lib/php4/20050606/gd.so' - /usr/lib/php4/20050606/gd.so: undefined symbol: gdImagePngCtx in Unknown on line 0**
[Sat Apr 22 18:24:09 2006] [notice] Apache/2.0.55 (Debian) PHP/4.4.2-1+b1 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
```

Any ideas? Thank you in anticipation!

---

### Post by sYs^ on 2006-04-23
Resolved by editing /etc/ld.so.conf and removing a wrong a line.

The 1st error is a known bug: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=357373](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=357373)

---

