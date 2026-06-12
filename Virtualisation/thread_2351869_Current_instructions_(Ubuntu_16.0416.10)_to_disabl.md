---
title: "Current instructions (Ubuntu 16.04/16.10) to disable netfilter for bridges (for KVM)"
date: 2017-02-07
forum: Virtualisation
---

### Post by jan-kaz on 2017-02-07
Hello,
I started playing with KVM and setup a few bridges and VLANs for VMs. I found some articles and examples but all of them are for old distributions.

I currently run KVM on Kubuntu 16.10 on my laptop with single NIC connected over USB. I know that this isn’t nice combination but it works for me for testing. I setup bridges and VLANs using great script in: [http://serverfault.com/questions/543434/multiple-different-vlan-trunks-to-kvm-guests-linux](http://serverfault.com/questions/543434/multiple-different-vlan-trunks-to-kvm-guests-linux)
since I can make if functional using static configuration in /etc/network/interfaces for some reason.

One thing that I’m struggling with is how to disable iptables processing for all bridges for security and performance reasons.

I found some old articles that have instructions to add to /etc/sysctl.conf:
```
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0
net.bridge.bridge-nf-filter-pppoe-tagged = 0
net.bridge.bridge-nf-filter-vlan-tagged = 0

```

This setup causes error when: sysctl -p


in man page [http://manpages.ubuntu.com/manpages/wily/man5/sysctl.d.5.html](http://manpages.ubuntu.com/manpages/wily/man5/sysctl.d.5.html)
I found probably more current instructions.

My current configuration is:

new file: /etc/udev/rules.d/99-bridge.rules:
```
ACTION=="add", SUBSYSTEM=="module", KERNEL=="br_netfilter", RUN+="/lib/systemd/systemd-sysctl --prefix=/net/bridge"

```

new file: /etc/sysctl.d/bridge.conf:
```
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0
net.bridge.bridge-nf-filter-pppoe-tagged = 0 # I added this, not specified in man page
net.bridge.bridge-nf-filter-vlan-tagged = 0  # I added this, not specified in man page

```

Could you please tell me, is it correct configuration? How can I check that the configuration works? Thank you.

---

### Post by rudolf.vesely on 2017-02-08
I tried something similar and iptables were not able to block bridge traffic so I assume it's correct.

---

### Post by wildmanne39 on 2017-02-08
*Thread moved to **Virtualisation**.*

---

### Post by solidus23 on 2018-01-08
So I have had this issue for a long time where the br_netfilter was keeping my VM's from connecting to the internet from my bridge adapter. I tried everything and search for weeks trying to find something. Only when disabling br_netfilter by setting 

net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0

seemed to make it work and it would work immediately when those settings were set. I had even tried the solution above and sometimes when I rebooted it would keep the settings but sometimes it wouldn't. Well I tried both solutions linked above ([http://manpages.ubuntu.com/manpages/wily/man5/sysctl.d.5.html](http://manpages.ubuntu.com/manpages/wily/man5/sysctl.d.5.html)) and it seems to now be working. What a pain. Thanks.

---

### Post by phil14 on 2018-01-22
On Xenial this works for me. (I use Xen, but the problem is the same.)

Create the file [FONT=courier new]/etc/modprobe.d/xen-bridge.conf[/FONT]

Contents:

[FONT=courier new]# XEN
# For performance and security reasons, it's highly recommended that
# netfilter is disabled on all bridges.

install br_netfilter /sbin/modprobe --ignore-install br_netfilter \
           && /bin/echo "0" > /proc/sys/net/bridge/bridge-nf-call-iptables \
           && /bin/echo "0" > /proc/sys/net/bridge/bridge-nf-call-arptables \
           && /bin/echo "0" > /proc/sys/net/bridge/bridge-nf-call-ip6tables
[/FONT]
Reboot. Job done.

---

