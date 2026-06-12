---
title: "iptables fatal error"
date: 2010-02-26
forum: Server Platforms
---

### Post by sebastiaands on 2010-02-26
Hi,
When I try to use iptables, for example:
```
iptables -L
```

I get the following error...
```
FATAL: Error inserting ip_tables (/lib/modules/2.6.31.6/kernel/net/ipv4/netfilter/ip_tables.ko): Unknown symbol in module, or unknown parameter (see dmesg)
iptables v1.4.4: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

I am using Ubuntu 9.10 server edition and iptables 1.4.4.

This is what dmesg says:
```
x_tables: disagrees about version of symbol seq_open_net
x_tables: Unknown symbol seq_open_net
x_tables: disagrees about version of symbol register_pernet_subsys
x_tables: Unknown symbol register_pernet_subsys
x_tables: disagrees about version of symbol init_net
x_tables: Unknown symbol init_net
x_tables: disagrees about version of symbol seq_release_net
x_tables: Unknown symbol seq_release_net
x_tables: disagrees about version of symbol proc_net_remove
x_tables: Unknown symbol proc_net_remove
x_tables: disagrees about version of symbol unregister_pernet_subsys
x_tables: Unknown symbol unregister_pernet_subsys
```

I tried removing iptables and installing it again, but that doesn't change anything...

Thanks,
Sebastiaan

---

