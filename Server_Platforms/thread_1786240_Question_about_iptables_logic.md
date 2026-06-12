---
title: "Question about iptables logic"
date: 2011-06-19
forum: Server Platforms
---

### Post by deanklear on 2011-06-19
I have this rule which works properly:

```

*nat
-A PREROUTING -i eth0 -p tcp -m tcp ! -d 192.168.100.150/32 --dport 80 -j REDIRECT --to-port 1000
```

However, now I need to exclude 192.168.100.151 from the same redirect, and I have simply run out of ideas in how to do this. Using a range does not seem to work.

I have tried separating it into different rules, and I'm afraid I may have a misunderstanding in which order rules are applied. Is there any easy way to say "for all tcp destined for 192.168.100.151, leave it alone" after or before redirecting all other traffic?

(Unfortunately this depends on a hard coded third party vendor, so I cannot separate it onto another subnet.)

---

### Post by BkkBonanza on 2011-06-20
Rules are applied in the order listed by -L option.
Have you tried to add a rule before this one that matches on the dest IP and has target ACCEPT so it doesn't get to this rule? I would think that should work. 

I think perhaps the REDIRECT target only recognizes matches on protocol and not dest IP (I'm not sure though).

---

