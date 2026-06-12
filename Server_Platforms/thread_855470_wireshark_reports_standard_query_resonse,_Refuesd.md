---
title: "wireshark reports standard query resonse, Refuesd"
date: 2008-07-10
forum: Server Platforms
---

### Post by Geran on 2008-07-10
I have two bind9 servers running that do forwarding, caching and hosting a few important domain name servers. Up until recently, everything was smooth, now whenever I send them a request that would need to be forwarded to a public dns server for lookup, I get this message in wireshark...

Standard query response refused

Not sure what's going on... can anyone help me figure the problem?

---

### Post by carcdrcdr on 2008-07-10
I know this is a stupid question: But have you tried bouncing bind?

---

### Post by Geran on 2008-07-10
It might not be, what do you mean by bouncing?

---

### Post by carcdrcdr on 2008-07-10
A bounce is a start and a stop.  Bind9 under Ubuntu should be: (to restart)
sudo /etc/init.d/bind9 stop
sudo /etc/init.d/bind9 start
or all at once:
sudo /etc/init.d/bind9 restart

---

### Post by Geran on 2008-07-10
yeah, tried that.

---

### Post by Geran on 2008-07-10
This all started when the server that my servers forward to went down for a bit, but it's back up now...

---

