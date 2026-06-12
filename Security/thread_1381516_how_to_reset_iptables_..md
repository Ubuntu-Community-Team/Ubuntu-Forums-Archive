---
title: "how to reset iptables ."
date: 2010-01-14
forum: Security
---

### Post by markp1989 on 2010-01-14
following instructions here: 

[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced)

i ran this ```


iptables -N rate-limit
iptables -A rate-limit -p tcp -m conntrack --ctstate NEW -m limit --limit 3/min --limit-burst 3 -j RETURN
iptables -A rate-limit -j DROP
iptables -I INPUT 1 -p tcp --dport 22 -j rate-limit
```

i am no longer able to ssh in to the machine , how can i reset iptables and firestarted back to default?

thanks Markp1989

---

### Post by HermanAB on 2010-01-15
$ sudo iptables -F

---

### Post by Lars Noodén on 2010-01-15
To really reset, remove all custom rules, custom chains and reset the default policies.

```

# IPv6

   ##
   ## set default policies to let everything in
   ip6tables --policy INPUT   ACCEPT;
   ip6tables --policy OUTPUT  ACCEPT;
   ip6tables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   ip6tables -Z; # zero counters
   ip6tables -F; # flush (delete) rules
   ip6tables -X; # delete all extra chains

# IPv4

   ## 
   ## set default policies to let everything in
   iptables --policy INPUT   ACCEPT;
   iptables --policy OUTPUT  ACCEPT;
   iptables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   iptables -Z; # zero counters
   iptables -F; # flush (delete) rules
   iptables -X; # delete all extra chains

```

---

### Post by Salimm on 2010-01-15
Thank you, Larz for the post

---

