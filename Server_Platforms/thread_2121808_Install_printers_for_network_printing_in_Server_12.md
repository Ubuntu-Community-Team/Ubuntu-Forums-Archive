---
title: "Install printers for network printing in Server 12.04"
date: 2013-03-03
forum: Server Platforms
---

### Post by lethalfang on 2013-03-03
The printer is automatically recognized and configured in Desktop edition, so I know that it works for Linux, but getting it work in the Server version is quite difficult. 

The server does recognize the USB device:
```

lsusb
Bus 005 Device 002: ID 0686:3006 Minolta Co., Ltd PagePro 1250W

```

I installed CUPS, but in any case, the printer is not installed in the OS:

```

lpstat -p
printer PDF is idle.  enabled since Fri 21 Dec 2012 10:19:35 PM PST

```

I don't know how to use the browser to access the thingie either:
[http://182.168.1.82:631](http://182.168.1.82:631) (local IP of my server)
**Forbidden**


Any gurus know what's up?


-----------------
Woohoo. Stupid me. I added a couple of "Allow all" to allow myself to add the printer via browser. It's working now.

---

