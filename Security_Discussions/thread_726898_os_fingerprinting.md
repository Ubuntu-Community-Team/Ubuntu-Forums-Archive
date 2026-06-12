---
title: "os fingerprinting"
date: 2008-03-17
forum: Security Discussions
---

### Post by adityaj on 2008-03-17
Hi

I am interested in an OS fingerprinting software which will tell if a machine is linux/windows/*nix not really interested in the exact versions of them. I used nmap but it takes too long. The problem is that the destination is mostly likely to drop all the icmp packets so xprobe2, sing not that useful. I was trying ettercap but not sure what options to give on the commandline (could use curses mode for the results but need to invoke from the commandline with no interaction). So any options other than these or a way where i can specify some other options to nmap so that it is faster.

Regards

Aditya

---

### Post by bswilson on 2008-03-17
If you think **nmap** takes too long, then you're doing it wrong.

---

### Post by adityaj on 2008-03-17
> **bswilson said:**
> If you think **nmap** takes too long, then you're doing it wrong.

Quite possible. nmap command

```
nmap -P0 -O2 target_host
```

---

### Post by jba6511 on 2008-03-17
nmap is really your easiest route. If you want to use a passive scanner you can try p0f. And as adityaj stated, use the -P0 switch to keep nmap from pinging the host.

---

