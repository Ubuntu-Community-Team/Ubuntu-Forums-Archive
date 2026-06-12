---
title: "iptables questions"
date: 2007-08-16
forum: Server Platforms
---

### Post by KevinM1 on 2007-08-16
I followed the "How To" on here to the letter, but my results aren't quite the same as those in that post.  In particular, the values in the 'prot' column that have the value 'all' in the example are '0' for me:
```

Chain INPUT (policy ACCEPT 3978 packets, 5431K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  315  150K ACCEPT     0    --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp dpt:www 
    2   120 ACCEPT     0    --  lo     any     anywhere             anywhere            
   19  4489 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/min burst 5 LOG level debug prefix `iptables denied: ' 
   29  6666 DROP       0    --  any    any     anywhere             anywhere
```

Is this okay, or is there a problem?  I really only want to limit possible connections to SSH and the web (including established sessions).

Thanks!

---

### Post by koenn on 2007-08-16
in an iptables listing such as the one you post, protocol # 0 means all/any protocol.

---

### Post by KevinM1 on 2007-08-16
> **koenn said:**
> in an iptables listing such as the one you post, protocol # 0 means all/any protocol.

Great, thanks! :)

---

