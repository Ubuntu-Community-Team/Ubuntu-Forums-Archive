---
title: "Slow/no response outside lan.  8.04 Apache"
date: 2009-02-28
forum: Server Platforms
---

### Post by Thirtysixway on 2009-02-28
I have 8.04 server edition with ports forwarded on my router.  I can access it fast on my lan, but the connection seems slow when I'm at places like the library.

The big issue is that when trying to access my site from a proxy like hidemyass.com or using wget on my webhost, it times out.

Anyone know why it's timing out?  could it be some type of firewall setup?  I currently have (moblock?) setup for torrent stuff and I have fail2ban installed and running.

Running 8.04 server, apache2 using virtual hosts.

---

### Post by jre on 2009-02-28
If it is Moblock you can simply check /var/log/moblock.log to see if your connection attempts were blocked. If yes, then you can configure MoBlock to accept certain connections.

---

