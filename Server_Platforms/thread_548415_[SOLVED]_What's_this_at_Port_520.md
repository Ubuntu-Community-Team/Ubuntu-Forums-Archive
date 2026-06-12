---
title: "[SOLVED] What's this at Port 520?"
date: 2007-09-11
forum: Server Platforms
---

### Post by nvteighen on 2007-09-11
Hi!

Could someone explain me if it's normal that a **computer** tries to connect to mine using (UDP) port 520? Iptables blocked the connection, but it seemed to me be very rare... the attempt came from a Windows computer at my home wireless; that computer constantly "bullies" my Ubuntu-box at Samba ports (blocked by iptables) and with Portmaps (also blocked), but this attempt at 520 is absolutely new.

I've researched about the port and found out that is used by **routers**. Didn't understand much, just that's a way to calculate the quickest path in a network... But this time it was not the router, but a computer...

Here is Firestarter's log:
```

Time: Sep 11 14:28:00 Source: 192.168.0.13 Destination: 192.168.0.255 In IF: eth1 Out IF:  Port: 520 Length: 52 ToS: 0x00 Protocol: UDP Service: Route
```

Thanks! (Just want to understand what happened)

---

### Post by southernman on 2007-09-11
[http://www.linuxquestions.org/questions/showthread.php?t=180341]("http://www.linuxquestions.org/questions/showthread.php?t=180341")

[http://www.google.com/search?q=Port%3A+520&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=Port%3A+520&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

Doesn't appear to be anything to worry about. FRom the log line you posted it's coming from the 192.168.0.13 (assumed to be the static ip of the server) and going to the gateway IP of the router (192.168.0.255)

---

### Post by nvteighen on 2007-09-11
> **southernman said:**
> [http://www.linuxquestions.org/questions/showthread.php?t=180341]("http://www.linuxquestions.org/questions/showthread.php?t=180341")

[http://www.google.com/search?q=Port%3A+520&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=Port%3A+520&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

Doesn't appear to be anything to worry about. FRom the log line you posted it's coming from the 192.168.0.13 (assumed to be the static ip of the server) and going to the gateway IP of the router (192.168.0.255)

Thanks! (Wow, those links where clear enough... Why haven't I found them?)

---

