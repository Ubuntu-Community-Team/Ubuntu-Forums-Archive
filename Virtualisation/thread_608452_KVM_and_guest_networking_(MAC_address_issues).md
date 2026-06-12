---
title: "KVM and guest networking (MAC address issues)"
date: 2007-11-10
forum: Virtualisation
---

### Post by Nuld on 2007-11-10
I followed the section "Virtual NICs on VDE, VDE Tap'd to Host, Tap NATed to Outside" in the Ubuntu [KVM networking documentation](https://help.ubuntu.com/community/KVM#head-db5235851cc1b9c712f99a074f02c91e8590c880-2) to enable my KVM guests to communicate with each other. Unfortunately, KVM assigns each virtual machine the same MAC address, which results in all guests getting the same IP address from the DHCP. Assigning static IP addresses doesn't help either in this case.

First I tried to assign each guest a different MAC address with the KVM option -net nic,macaddr=... This causes the network interface in the guest to be disabled and trying to enable it with ifup eth0 results in the following output:

```
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
```

Then I tried to specify the MAC address using the tool macchanger in the guest system. This seems to work at the first glance, the interface comes back up with the new MAC address. But it doesn't get an IP address from the DHCP and when I specify a static IP address neither the host nor other guests can ping the guest system.

Any suggestions how I can get this to work? I simply want the guests and the host to be able to communicate with each other.

Thanks!

---

### Post by Nuld on 2007-11-12
Has nobody set up networking between KVM guests yet? I could really use some advices.

---

### Post by Nuld on 2007-11-13
Okay I figured it out. I have to specify the macaddr option to KVM when I am installing the OS in the virtual machine and can't simply change it later and expect the guest system to detect the change and configure the new card as eth0.
Can someone tell me how I can do this without having to setup all the virtual machines again? I probably just have to specify that the new network card (new MAC) is supposed to be eth0 from now on... But how? :) 

Thanks.

---

### Post by Nuld on 2007-11-13
Okay I figured that out as well. In case someone else is trying to do the same thing: the assignment of network cards to interfaces is done in /etc/udev/rules.d/70-persistent-net.rules.

---

### Post by rdibley on 2008-10-17
Thanks for the information, despite the fact that nobody replied to you!  I was banging my head against the wall all morning (figuratively speaking) trying to figure out why changing the MAC on my KVM guest was causing the network to stop working.  I found a similar file within the /etc/udev/rules.d/ directory and deleted the entries.  Everything works great now!

---

