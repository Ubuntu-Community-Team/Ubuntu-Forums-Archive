---
title: "ufw default policy"
date: 2008-08-24
forum: Security
---

### Post by Steve1961 on 2008-08-24
I've been using firestarter for a number of years and on the whole I've been quite happy with it.  However, I've recently started using a pptp vpn and I couldn't get firestarter to work with it, despite using the workarounds on the firestarter web page.  So I switched to guarddog and this works Ok with the vpn.  However, as neither firestarter or guarddog seem to be actively developed at the moment I thought I'd also look at uwf and the guwf gui.

Anyway, after reading the various web and man pages for ufw I'm unclear about the default policy when set to deny.  My understanding is that initially ufw allows all incoming and outgoing connections, until the default policy is changed to deny.  But once set to deny does this just apply to incoming connections and leave all outgoing connections enabled (as firestarter does) or is everything disabled in both directions until rules are added?

---

### Post by Nepherte on 2008-08-24
It only applies to incoming connections.

---

### Post by Steve1961 on 2008-08-24
> **Nepherte said:**
> It only applies to incoming connections.


Excellent, that makes things a whole lot easier than opening ports for everything you need.  many thanks.

---

