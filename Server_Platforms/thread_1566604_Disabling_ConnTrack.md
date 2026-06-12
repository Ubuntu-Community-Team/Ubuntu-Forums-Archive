---
title: "Disabling ConnTrack"
date: 2010-09-02
forum: Server Platforms
---

### Post by Kyrra on 2010-09-02
I've got a webserver I'm running that isn't all that powerful (it's a VPS).  I've seen a recent spike in traffic and notice and noticed the following in my messages file:

> Sep  2 12:37:53 www kernel: [1004617.253819] __ratelimit: 106 callbacks suppressed
Sep  2 12:37:53 www kernel: [1004617.253826] nf_conntrack: table full, dropping packet. (as an aside, I found where I had the conntrack_max set too low, so I raised it so I won't get these drops anymore)

I'm not doing NAT at all, but I am running an iptables based software firewall.  Should I just be able to disable/unload the conntrack kernel module?

If so, how exactly would I go about removing this kernel module?


Thanks,
-Kyrra

---

### Post by BkkBonanza on 2010-09-02
I don't think you need to remove the module but instead any iptables rules using that module. If you remove the module and there are iptables rules using it then you'll get errors. For a firewall contrack is almost essential since I think it is needed to handle the related,established criteria used to allow inbound traffic for outbound connections. 

I could be wrong about that and I suppose you could try removing it and see if it breaks. Anyway the **modprobe -r ...** command is for removing a module, and **lsmod** for listing them. But this does assume the module is dynamically loaded. If it is compiled into your kernel then you can't do it.

---

### Post by Kyrra on 2010-09-07
Thanks BkkBonaza.  I was guessing conntrack may be used for these rules, but I wasn't really sure.  Makes sense though.  Guess I'll just have to monitor my usage and hope I don't go over.

---

