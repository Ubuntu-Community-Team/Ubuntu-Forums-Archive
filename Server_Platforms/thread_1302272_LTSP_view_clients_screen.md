---
title: "LTSP view clients screen"
date: 2009-10-26
forum: Server Platforms
---

### Post by map7 on 2009-10-26
I've setup LTSP 5 on top of my Ubuntu 904 32bit and have two clients so far off this connection.  I would like to have the ability to VNC to the clients so that I can help them remotely.  I've enabled 'Remote Desktop' on the client but I cannot connect to it using vnc.

I checked with nmap on my clients IP and all that is open is one port:
```

Interesting ports on 192.168.200.209:
Not shown: 999 closed ports
PORT     STATE SERVICE
6007/tcp open  X11:7

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds

```

Is it possible to connect?  Do I have to open up a service for clients somewhere?

---

### Post by jason_Xtreme on 2009-10-27
Install ITALC check the edubuntu docs for config tho it should work out of the box.

---

### Post by map7 on 2009-10-28
Thanks for that suggestion I found that ITALC is exactly what I wanted.

---

