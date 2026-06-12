---
title: "webserver problem"
date: 2008-01-16
forum: Server Platforms
---

### Post by radiofanatic on 2008-01-16
I registered two domains with my server ip ( one is .eu and the other .ro ) but they dont get associated with my server ip ... If I ping anyone of them it doesnt resolve it. Even if I ping from server to 127.0.0.1 or my server ip I get no answer but if I ping from a remote machine the server ip responds.
What is the problem ?
Sorry for my english

LE : I resolved the problem with pinging in 127.0.0.1 or ip with those commands : "ifdown lo" and then "ifup lo" . Now I wait to see if the domains get associated with server ip.

---

### Post by r00tintheb0x on 2008-01-16
Have you edited your DNS settings for the domain name?

---

### Post by radiofanatic on 2008-01-17
where do I need to configure the dns settings ? :confused:

---

