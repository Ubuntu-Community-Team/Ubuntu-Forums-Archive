---
title: "Problem Configuring Apache as a Local Server"
date: 2006-04-03
forum: Server Platforms
---

### Post by shawnhcorey on 2006-04-03
I have download apache2 via the Synpatic Package Manager and tried to get t to work. It seems to run fine, but I can't access it via my browser. When I try `http://127.0.0.1/`, it just times out.

I have place my configuration files on my Wiki page at [https://wiki.ubuntu.com/Shawnhcorey/ApacheAdventure](https://wiki.ubuntu.com/Shawnhcorey/ApacheAdventure)

I have read the Ubuntu Server Doucmentation and the Apache documentation, but still don't known what I'm doing wrong. Can anyone help?

shc

---

### Post by simplyw00x on 2006-04-04
Check /var/log/apache2/error.log

---

### Post by shawnhcorey on 2006-04-04
Here is my /var/log/apache/error.log in its entirety:

[Mon Apr 03 09:24:12 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon Apr 03 09:35:54 2006] [notice] caught SIGTERM, shutting down
[Mon Apr 03 11:37:47 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon Apr 03 11:52:19 2006] [notice] caught SIGTERM, shutting down
[Mon Apr 03 11:56:25 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon Apr 03 11:57:25 2006] [notice] caught SIGTERM, shutting down
[Mon Apr 03 12:12:43 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon Apr 03 12:13:53 2006] [notice] caught SIGTERM, shutting down
[Mon Apr 03 12:16:21 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon Apr 03 12:23:30 2006] [notice] caught SIGTERM, shutting down
[Mon Apr 03 14:27:47 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon Apr 03 16:47:29 2006] [notice] caught SIGTERM, shutting down
[Mon Apr 03 16:49:13 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Tue Apr 04 00:43:06 2006] [notice] caught SIGTERM, shutting down
[Tue Apr 04 09:41:35 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Tue Apr 04 12:33:29 2006] [notice] caught SIGTERM, shutting down
[Tue Apr 04 12:35:18 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations

Not very enlightening it is. Apache is just not seeing any requests.

shc

---

### Post by aschuete on 2006-04-04
Assuming that your server is setup on a router along with the rest of the local computers, is your router forwarding port 80 to your server's local IP.

---

### Post by shawnhcorey on 2006-04-04
I don't think you understand what I'm trying to do. I set my Listen 127.0.0.1:80 so it will respond to only request from my machine. I need to do some testing and I don't want it to respond to anyone else.

I don't have a router but I have a bridge to my DSL modem. But perhaps you're right, the browser is not looking on the localhost.

I had this setup before on MacOSX with Apache v1.3 but I can't seem to get it on Ubuntu with Apache v2 :(

sgc

---

### Post by fdoving on 2006-04-14
I can see from your wiki that you got it working. :)

To automagically bring up lo at boot, add:
```

auto lo

```

to /etc/network/interfaces.


- Frode

---

