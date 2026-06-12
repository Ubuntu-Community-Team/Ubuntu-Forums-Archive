---
title: "encrypteing logs in transit rsyslog"
date: 2022-12-26
forum: Security
---

### Post by ant2ne on 2022-12-26
What I'm imagining is the rsyslog client and server sharing peer certificates, not CA. A CA would be more overhead and more difficult to manage. I'd rather not use stunnel, but I would like something like its functionality, without all the port bouncing and stuff.

All I can find on "the googles" is CA type certs and not self signed or peer <-> peer certs. Is this possible? Can someone direct me to a good tutorial? Thanks?

---

### Post by TheFu on 2022-12-28
Doesn't journalctl do remote logging?  It is built into every systemd-based Linux. Journalctl is one of the good things about systemd.

[https://www.freedesktop.org/software/systemd/man/systemd-journal-remote.service.html](https://www.freedesktop.org/software/systemd/man/systemd-journal-remote.service.html)  

> For transport over the network, this serialized stream is usually carried over an HTTPS connection.

---

### Post by ant2ne on 2022-12-28
i kinda need to stay with rsyslog

---

### Post by ant2ne on 2022-12-29
I have been googling, and I am starting to think that this can't be done without a CA. many of the devices will be inside a DMZ and not access to a CA. I was hoping I could use peer certs, but I can't find documentation on how to do this. Years ago I have used stunnel with peer certs to bounce logs. But I was hoping that rsyslog would have something built in that can do what I require.

---

