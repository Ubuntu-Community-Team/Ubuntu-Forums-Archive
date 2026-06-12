---
title: "[SOLVED] proftpd not starting..."
date: 2007-08-27
forum: Server Platforms
---

### Post by flipjarg on 2007-08-27
I recently installed **proftpd** and right after the installation it attempted to start automatically. Here is the error message I received:

```
 - IPv6 getaddrinfo 'obnog.com' error: Name or service not known
c-22-xx-xx-xxx.hds1.mi.comcast.net - fatal: Socket operation on non-socket
```

I've tried using **MasqueradeAddress** but it doesn't make a difference.

I'm running this server on a router. I've set up "Virtual Hosting" . HTTP traffic from the web passes through to the server with no problem. I've set up all HTTP, FTP traffic to go to the server with a static IP address on the network.

I've messed with my /etc/hosts file but haven't got any new error messages from changes i've made.

I do not know why proftpd will not start. Any suggestions?

---

### Post by freebeer on 2007-08-27
This might help:

```

5. "Fatal: Socket operation on non-socket"

You have ProFTPD configured to run in inetd mode rather than
 standalone. In this mode, ProFTPD expects that it will be run from
the inetd super-server, which implies that stdin/stdout will be sockets 
instead of terminals. As a result, socket operations will fail and the above
 error will be printed. If you wish to run ProFTPD from the shell, in 
standalone mode, you'll need to modify your proftpd.conf configuration 
file and add or edit the ServerType directive to read:

ServerType standalone

```

from: [http://www.proftpd.org/docs/faq/linked/faq-ch4.html#AEN273](http://www.proftpd.org/docs/faq/linked/faq-ch4.html#AEN273)

---

### Post by flipjarg on 2007-08-27
I still get:

```
- IPv6 getaddrinfo 'obnog.com' error: Name or service not known
```

Any suggestions for that? I've found some info on it but nothing has worked yet.

---

### Post by Gruelius on 2007-08-27
I cant search at the moment but i remember there being a line about forcing IPV4 for my setup.

Ah found it

Add this to the top of the conf file
"UseIPv6 off" without the talking marks.

---

### Post by freebeer on 2007-08-27
Yeah.. I get that but it's a warning, not a fatal error.  Still works fine without it.  (I should have mentioned that.)

Thanks for the tip, Gruelius!

---

### Post by flipjarg on 2007-08-27
With **UseIPv6 off** I receive no errors!!! SOLVED

---

