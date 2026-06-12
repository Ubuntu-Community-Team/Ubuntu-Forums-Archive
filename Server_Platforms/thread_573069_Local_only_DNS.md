---
title: "Local only DNS"
date: 2007-10-11
forum: Server Platforms
---

### Post by Sir8 on 2007-10-11
Hi All,

I'm trying to setup an intranet site within a LAN, and instead of using IP address, want to assign a name eg aintranet, using a local DNS server.

Can anyone point me to some related sites I can follow on this?

Most documentation assumes the DNS server is used as an internet dns requiring FQDN.

Any assistance is much appreciated.

Tks
Boris

---

### Post by HermanAB on 2007-10-11
If it is a LAN with less than 10 machines then you can put it in the hosts files.

If you have more than 5 machines, then install BIND and put it in a zone file.

Cheers,

Herman

---

### Post by netlogic on 2007-10-11
For something like this dnsmasq is perfect. It is so easy to setup and it uses a centralized host file.

---

### Post by Sir8 on 2007-10-15
Still struggling with Bind9 perhaps i'm a newbie.
But dnsmasq works ... cool. Tks for the help really appreciate it.

---

