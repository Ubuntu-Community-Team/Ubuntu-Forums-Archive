---
title: "Firewall against DOS"
date: 2010-09-29
forum: Security
---

### Post by hosseinyounesi on 2010-09-29
Hi,

How can I setup a firewall against DOS attacks in ubuntu? Is there any software or I have to it?!

Thanks b4

---

### Post by teejaybee on 2010-09-29
DoS attacks come in many shapes and forms. If they are sending large volumes of traffic your way, there is no way to stop it unless someone upstream from you does it (eg. your ISP). If they are flooding your http etc. server with requests then you can firewall that port off to try and lessen the impact.

---

### Post by kreggz on 2010-09-29
If you are interested here is some more reading material -

For a Server: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

For a Desktop: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

In general: [https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

---

### Post by HermanAB on 2010-09-29
Iptables has a rate limit filter that is really easy to use.

---

