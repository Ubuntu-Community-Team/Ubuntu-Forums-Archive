---
title: "how to enable two vcpu's in Dom0 with xen?"
date: 2017-04-03
forum: Virtualisation
---

### Post by minimike2 on 2017-04-03
Hi there

By booting Ubuntu 16.04 with XEN I've only one CPU available. I think thats an good choise in many scenarios. But for my current project I need the power of two vcpu's on Dom0. What I have to do to get that?
I've tried with

```

xl vcpu-set 0 1
xl vcpu-pin 0 1 all all

```

```

xl vcpu-list
Name                                ID  VCPU   CPU State   Time(s) Affinity (Hard / Soft)
Domain-0                             0     0    0   r--     388.1  all / all
Domain-0                             0     1    -   --p       0.0  all / all

```

But the second core still does not run.

thanks in advance

---

### Post by TheFu on 2017-04-03
[https://wiki.xen.org/wiki/Dom0](https://wiki.xen.org/wiki/Dom0)
[https://wiki.xen.org/wiki/Tuning_Xen_for_Performance#Dom0_vCPUs](https://wiki.xen.org/wiki/Tuning_Xen_for_Performance#Dom0_vCPUs) 
Or am I missing something?

---

### Post by minimike2 on 2017-04-21
yes you have forgotten something. Because I can use only one cpu but two are enabeled.

---

