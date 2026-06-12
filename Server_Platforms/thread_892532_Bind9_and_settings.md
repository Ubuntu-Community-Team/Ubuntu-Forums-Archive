---
title: "Bind9 and settings"
date: 2008-08-17
forum: Server Platforms
---

### Post by andyd34 on 2008-08-17
I have bind9 installed on one of my boxes, When I change the settings where my name is registered do I do it as follows

NameServer ns1.mydomain.name
NSIP ***.***.***.*** (lan IP 192.***....) or (ip 82.***....)

---

### Post by windependence on 2008-08-17
Well you can do that but it certainly isn't necssary or even desirable to have your own nameservers. It would probably be best and easiest to just use the ones your registrar have. It just adds complexity to your setup unless you are running a huge server farm.

-Tim

---

### Post by andyd34 on 2008-08-17
But can i still install an emailserver

---

### Post by windependence on 2008-08-17
Sure, you don't need a DNS server for that either. Quite frankly I don't know where all this BIND9 nonsense is coming from. I think there may be tutorials out there that are suggesting that but with a mail server, you just point your MX records at your mail server. For outgoing SMTP you don't even need that.

-Tim

---

