---
title: "Server (apache) just won't load for users"
date: 2007-02-02
forum: Server Platforms
---

### Post by ashleywalton on 2007-02-02
I've had Apache set up and running for a while and life was all going great. Life was a breeze... until someone told me it wasn't actually working. The first problem was the file permissions, which I've got sorted out, but right now my problem is the pages just won't load. That's it. Sometimes people get a gray screen (conviently enough, the background of my layout is gray), or sometimes they get an "unable to connect to server" error. Meanwhile, I can access just fine. 

I thought it may be the server timing out too early, but I've since uploaded it to 9000 seconds, however, that seems to be doing more bad than good (at 1000 seconds they got the gray screen, but anything higher would just time out)

Any fixes for this?

---

### Post by elst on 2007-02-03
You need to narrow the problem down a bit more. The Apache logs are actually helpful and pretty detailed. If your Web site is driven by a database then there may be an issue there, rather than with the Web server.

---

### Post by ashleywalton on 2007-02-03
There's no database even installed right now, so that can't be the issue. 

But here's a couple of recent bits from my error.log:

```

[Fri Feb 02 20:19:53 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Fri Feb 02 20:22:50 2007] [notice] Graceful restart requested, doing restart
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Feb 02 20:22:51 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Fri Feb 02 20:26:08 2007] [notice] Graceful restart requested, doing restart
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Feb 02 20:26:09 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Fri Feb 02 20:30:40 2007] [notice] SIGHUP received.  Attempting to restart
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Feb 02 20:30:41 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Fri Feb 02 22:50:44 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 07:18:53 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Sat Feb 03 07:50:54 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 08:39:19 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Sat Feb 03 09:06:43 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 10:48:23 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations
[Sat Feb 03 11:20:09 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 11:39:40 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations

```

I have no Idea what SIGTERM means, I Googled it up a bit, and it seemed to be caused by modules? But I don't think I've installed any modules (except for PHP).

---

### Post by elst on 2007-02-03
SIG(nal) TERM(ination) - it's been signalled to shut down and is complying with the request. The man page for "signal" explains the signals.

The "ServerName" issue may be caused by an incorrect hostname - it's worth checking that your server is using a fully qualified domain name as it's hostname, and that forward and reverse DNS lookups produce the right results.

---

