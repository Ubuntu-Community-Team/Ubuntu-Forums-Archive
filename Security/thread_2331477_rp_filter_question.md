---
title: "rp_filter question"
date: 2016-07-22
forum: Security
---

### Post by rtwo2 on 2016-07-22
Hi

Which command would bring me an output like this? I'd like to see if rp_filter is enabled in my Linux box. addressing is ipv6. 

Chain rpfilter (1 references)

pkts bytes target     prot opt in     out     source               destination

0     0 rplog      all  --  *      *       0.0.0.0/0            0.0.0.0/0      
     rpfilter validmark invert ctstate INVALID,NEW,RELATED

---

### Post by steeldriver on 2016-07-22
I'm not familiar with rp_filter, but you should be able to list iptables rules by chain name using the syntax

```

iptables [-t table] -L [chain [rulenum]] [options...]

```

e.g.

```

sudo iptables -L rpfilter

```

---

### Post by rtwo2 on 2016-07-22
> **steeldriver said:**
> I'm not familiar with rp_filter, but you should be able to list iptables rules by chain name using the syntax

```

iptables [-t table] -L [chain [rulenum]] [options...]

```

e.g.

```

sudo iptables -L rpfilter

```


root@Firewall:~# iptables -L rpfilter
iptables: No chain/target/match by that name.

---

