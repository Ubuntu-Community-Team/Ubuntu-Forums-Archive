---
title: "Blacklist host"
date: 2008-01-15
forum: Server Platforms
---

### Post by Dr Small on 2008-01-15
So if I found that I was getting attacked on a certain port, and wanted to block that host from connecting to my server, how would I go about doing this?

I really didn't want to have this automatic, (and from what little I have read, this is what denyhosts does), but I just wanted to be able to manually blacklist the host(s) as I see them attacking my server.

What would be the best method to use for this?

Dr Small

---

### Post by foxylad on 2008-01-15
Check out iptables. This is a firewall built into the kernel so it is very fast and efficient, but there isn't a gui so if you are not used to the command line, you will have difficulty. Firestarter may also help you.

---

