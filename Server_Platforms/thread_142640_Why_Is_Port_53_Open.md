---
title: "Why Is Port 53 Open?"
date: 2006-03-10
forum: Server Platforms
---

### Post by OffHand on 2006-03-10
Hi

I just ran a Shields Up scan and it tell me port 53 (DNS) is open.
Now I cannot remember I installed or activated a DNS so can
anyone explain to me how to stop/close this?

Thanx in advance,
Subsonic

P.S. Due to timezone I might not respond right away.

---

### Post by drogoh on 2006-03-10
Don't worry about it.  If you just *have* to get rid of that one open port, run 'netstat -nap', look at what is listening on 53 and disable it.

---

### Post by OffHand on 2006-03-11
Thnx for your reply. I tried that command but the list it gave me didn't make much sense to me. What I don't get is that everyone tells me I don't need a firewall because nothing is open/listening but this doesn't seem to be true. At least my configuration. And now you tell me it's not a big deal it's open. I'm a bit confused.

---

### Post by curtis on 2006-03-12
It is probably open not on your computer, but on your ISPs switch or your router.

---

### Post by ssam on 2006-03-12
are you using network manager? that installs a DNS server

---

