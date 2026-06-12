---
title: "KVM with 2 external ips"
date: 2011-10-20
forum: Virtualisation
---

### Post by Kamzi on 2011-10-20
So, the thing is. I would like to run one virtual machine with KVM on my Ubuntu 11.10 Oneiric ocelot server. Running virtual machine isn't the problem, problem is that I would like both physical and virtual machines to have own external ips. I made one virtual bridge but now it shows only one external ip and one internal :192.168.122.1.

I have googled pretty much but haven't seen any solution to this. Could someone be so nice and tell how to do this?

---

### Post by elsalvador on 2011-10-20
Hi Kamzi

I am having similar questions but mine are both internal addresses....

Network Manager just doesn't seem to play with bridging at all, is that what you've found?

I tried doing the /etc/network/interfaces config as found in lot sof places, but it seemed to use br0 as the outgoing interface for everything, rather than eth0, so lots of stuf broke.

I'm sure it *should* work, but something seems broken in 11.10, maybe the answer will be "11.04", I hope not....

Good luck - would appreciate your comments!
elsalvador (no relation)

---

### Post by Kamzi on 2011-10-20
> **elsalvador said:**
> Hi Kamzi

I am having similar questions but mine are both internal addresses....

Network Manager just doesn't seem to play with bridging at all, is that what you've found?

I tried doing the /etc/network/interfaces config as found in lot sof places, but it seemed to use br0 as the outgoing interface for everything, rather than eth0, so lots of stuf broke.

I'm sure it *should* work, but something seems broken in 11.10, maybe the answer will be "11.04", I hope not....

Good luck - would appreciate your comments!
elsalvador (no relation)


Well, I'm myself running server edition so no network nightmare here.I have everything running through that br0 but I haven't seen any problems.

---

