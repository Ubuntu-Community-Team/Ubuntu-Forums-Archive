---
title: "simple network traffic monitor and logger"
date: 2007-07-25
forum: Server Platforms
---

### Post by Krijk on 2007-07-25
I'm looking for a simple network traffic logger that logs to a textfile or directly to a database.

It should be able to log the following:
[LIST]
[*]start date/time session
[*]end date/time session
[*]source ip and port
[*]destination ip and port
[*]protocol
[/LIST]

I've been looking at available tools, but the one's I found were either to complex or to simple. Netflow seems to be able to do this, but I don't know if that can be used with Linux. 

Tcpdump also provides usefull information, but logfiles generated with it become very large.

Does anybody have suggestions?

---

### Post by tim356 on 2007-07-25
Ethereal/Wireshark?

---

