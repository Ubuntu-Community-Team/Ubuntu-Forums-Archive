---
title: "Slapd(openLDAP) refuses connections"
date: 2010-05-24
forum: Server Platforms
---

### Post by denarced on 2010-05-24
I have slapd-server running but it seems to refuse connections in a very odd way. Wireshark shows that everytime JavaEE-client tries to connect, only 2 packages are sent. As I understand, in tcp/ip protocol, the first is just "hello, who's there". The last is just a message consisting of ACK and RST. I think RST means "we're done". At this point I don't think any credentials are checked so I don't know what could be wrong ??

Help much appreciated :)

---

### Post by denarced on 2010-05-25
Hah .. there was a problem with the configuration.
No-one was listening to the port 389.
Correction to /etc/default/slapd or /etc/default/ldap
did the trick .. can't remember which file it was

---

