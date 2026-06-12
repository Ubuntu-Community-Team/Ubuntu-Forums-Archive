---
title: "high network latency (lan, bridge etc)?"
date: 2011-01-26
forum: Server Platforms
---

### Post by datamove on 2011-01-26
Dear colleges!

I have installed Ubuntu 10.10 server on a very recent dual-cpu 24 core  AMD Opteron server and provisioned guest VMs with KVM. The rest of the ubuntu config was practically not touched.

What I observe is rather high network latency, as measured by ping, in the system.

For example, ping to a loopback interface gives ~50 microseconds, while I measure ~10 on CenOS-5/Xeon server. Also, pinging a VM that is connected to a default bridge created by libvirt gives 500 microseconds, while it's ~100 on that CentOS5/Xeon machine. I've also setup a tap devise for a VM network connection, to avoid the bridge, but this made no difference.

Such a latency is unfortunately a performance killer for host to guest networking.

I have disabled apparmor in kernel and relaxed security settings in libvirt, but see no improvement.

setting up net.ipv4.low_latency=1 doesn't help also.

Any ideas on what might be wrong with the setup? 

Thanks in advance,
Artem.

---

