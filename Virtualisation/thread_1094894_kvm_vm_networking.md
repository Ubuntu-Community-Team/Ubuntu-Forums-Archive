---
title: "kvm vm networking"
date: 2009-03-13
forum: Virtualisation
---

### Post by el_baby on 2009-03-13
Well,

I finally [thread=1090853]could connect to my VMs[/thread].

Situation:

VMs created according to [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) (ubuntu 8.10 VM within an ubuntu 8.10 host. All done remotel via ssh).

Bridge configured and working in the host.

If I create a VM to use dhcp to get its address from the host's dhcp server (dnsmasq) I get no IP address (eth0 is up but no IP assigned to it).

If I create a VM using a fixed IP (192.168.122.2), the IP is configured OK and so is the routing (default route through 192.168.122.1). I can ping itself from inside (that is, **ping 192.168.122.2** works inside the VM but I **can't** ping the host from the VM or viceversa.

Is there something I'm missing in the configuration of the VM so that it sees the host?

Should bridging **also** be configured **inside** the VM?

TIA

---

