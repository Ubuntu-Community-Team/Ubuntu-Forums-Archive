---
title: "Bridging an interface for a soft-wall vm (no DHCP from modem)"
date: 2009-04-21
forum: Virtualisation
---

### Post by KamakazieX on 2009-04-21
I have an ubuntu 8.10 server with a virtualbox clarkconnect 4.3 community guest. I have the network setup as follows:

Ubuntu host 10.1.1.254 br0
ClarkConnect bridge to br0 (to host nic) 10.1.1.250

External (cable modem) host *manual unconfigured br1

both are using tap and the latest sun virtualbox-2.2 .deb release

The internal infrastructure is perfect, but the VM will not grab a dhcp address from the cablemodem.. I am wondering if I am missing any steps? Can I hide the host mac address from the modem? I know my isp limits 2 mac addresses which I thought might be the issue. I've tried to enter the same mac address in the vm as the unused host nic but it doesnt seem to work.

---

### Post by KamakazieX on 2009-04-21
bump

---

### Post by FrankT-Qc on 2009-04-21
Your ISP should not be aware of MAC addresses.

You might want to consider routing (maybe NAT?) if you want multiple machines on the same connection.

Besides, could you post the output of :
```

brctl show
ip address show

```

---

