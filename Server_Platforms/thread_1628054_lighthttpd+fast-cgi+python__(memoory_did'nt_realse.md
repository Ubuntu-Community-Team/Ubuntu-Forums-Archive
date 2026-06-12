---
title: "lighthttpd+fast-cgi+python  (memoory did'nt realse by lighttpd )"
date: 2010-11-22
forum: Server Platforms
---

### Post by aliahsan81 on 2010-11-22
Hi All

I have lighthttpd in production.I am facing issue that after X amount of time lighttpd consume all system memory and make server very unstable and sluggish.We are running lighttpd with fast-cgi and python At time we also get internal server error.Can any one guide me in memory management of lighttpd.

---

### Post by wongo888 on 2010-11-22
I've heard that this is a common problem with lighty. Have you considered nginx?

```

$ apt-cache show nginx
Package: nginx
Priority: optional
Section: universe/web
Installed-Size: 800
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Jose Parrella <bureado@debian.org>
Architecture: i386
Version: 0.7.65-1ubuntu2
Provides: httpd
Depends: libc6 (>= 2.4), libpcre3 (>= 7.7), libssl0.9.8 (>= 0.9.8k-1), zlib1g (>= 1:1.1.4), lsb-base (>= 3.2-14)
Suggests: ufw
Filename: pool/universe/n/nginx/nginx_0.7.65-1ubuntu2_i386.deb
Size: 335486
MD5sum: 68e0db05e0da8017c39ef1befbb84670
SHA1: d055c1ee78b2e854e855e6ad722a79f26a647ecb
SHA256: cc1078cff69b3b0553ca86d65cf018f4ab06eeda8e612b8fdbbb50af14030ee7
Description: small, but very powerful and efficient web server and mail proxy
 Nginx (engine x) is a web server created by Igor Sysoev and kindly provided to
 the open-source community. This server can be used as standalone HTTP server
 and as a reverse proxy server before some Apache or another big server to
 reduce load to backend servers by many concurrent HTTP-sessions.
 .
 It can also act as a POP3/IMAP mail proxy with SSL and TLS SNI support.
Homepage: http://nginx.net
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

This page has some possibly helpful config settings:

[http://redmine.lighttpd.net/issues/758](http://redmine.lighttpd.net/issues/758)

---

### Post by Suparious on 2010-11-22
This issue may not be Ubuntu specific.

Consider posting your question on the Lighttpd forums:
[http://redmine.lighttpd.net/projects/lighttpd/boards]("http://redmine.lighttpd.net/projects/lighttpd/boards")

---

