---
title: "[SOLVED] Just a quick question"
date: 2008-01-06
forum: Server Platforms
---

### Post by Techwiz on 2008-01-06
Does the iptables firewall (the one that firestarter manages) run 24/7 even without me keeping firestarter running?
Thank you.

---

### Post by HermanAB on 2008-01-06
Yes.

Firestarter is a GUI front end for iptables, which is a text front end for netfilter.  Netfilter is a kernel module (actually several kernel modules).  Once netfilter is configured it will keep doing its thing and doesn't need iptables or firestarter to be around.

Cheers,

Herman

---

### Post by Techwiz on 2008-01-07
Ok, thanks! :)

---

