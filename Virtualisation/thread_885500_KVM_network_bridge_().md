---
title: "KVM network bridge (?)"
date: 2008-08-10
forum: Virtualisation
---

### Post by noof on 2008-08-10
I have a server with two NICs, one to my ADSL modem and one to the local network. The server is used as router. The nice thing about my ISP is that I get 5 dynamic IPs. I want to run XP in KVM and make it get one IP from my ISP and one from linux on my local network. Like this:

```

        eth1                       eth2
host    85.x.y.z (dhcp from ISP)   10.0.17.1 (static)
kvm     85.x.y.w (dhcp from ISP)   10.0.17.x (dhcp from linux)
```

What's the best way to do this? Bridge eth1 to br0 and br1 and eth2 to br2 and br3, and use br0 and br2 with host and br1 and br3 with kvm? Is that even possible?

---

