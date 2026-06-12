---
title: "Apache SSL error"
date: 2009-12-24
forum: Server Platforms
---

### Post by spikoley on 2009-12-24
I am trying to set up SSL on Apache with a Karmic Koala server.  When I visit the https version of the site I receive a non descriptive error page.  I don't see any errors when starting Apache, but /etc/log/apache/error.log produces the errors below.

> [Thu Dec 24 14:13:42 2009] [notice] Graceful restart requested, doing restart
[Thu Dec 24 14:13:42 2009] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
[Thu Dec 24 14:13:45 2009] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.3 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g configured -- resuming normal operations
[Thu Dec 24 14:13:53 2009] [notice] caught SIGTERM, shutting down
[Thu Dec 24 14:13:58 2009] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.3 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g configured -- resuming normal operations


Googling hasn't help and I have been bang my head against the wall for a couple of hours.  I am unsure which config files to post, so let me know what I should post.  Any help is appreciated.

---

### Post by spikoley on 2009-12-25
I started over and it work.  I am not sure what caused this error.

---

