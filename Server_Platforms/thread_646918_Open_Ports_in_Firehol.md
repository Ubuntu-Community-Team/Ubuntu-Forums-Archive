---
title: "Open Ports in Firehol"
date: 2007-12-21
forum: Server Platforms
---

### Post by mmadd29 on 2007-12-21
Greetings all,

I have Firehol version 5 running on Ubuntu Gusty.  I have VNC installed, and to get it to accept connects I had to put this line in the firehol.config file:

server all accept

Prior to this it would not accept connections.  I tried:

server x11vnc accept, but no go.

It tell me I need to define VNC as a service.

What command do I use in firehol to only allow a connection on port 5900?

Thanks to all.

---

### Post by wormser on 2007-12-22
I am unfamiliar with Firehol.  I have used Firestarter and it is really easy.  It will set up an icon under system> administration.

```
sudo apt-get install firestarter
```

---

### Post by zbot on 2008-03-16
server vnc accept

-Zbot_1

---

