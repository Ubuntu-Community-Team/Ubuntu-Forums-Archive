---
title: "Do I need a vpn inside VM if I already have Host machine vpn?"
date: 2022-02-08
forum: Windows
---

### Post by h4lman on 2022-02-08
I run a windows 10 machine with a vpn.  I am new to virtual machines.  I set one up and it works.  All traffic seems to be routed through the host machine vpn.  Websites show that I'm using the host machine vpn.  Do I need an additional vpn inside the virtual machine?  That would really slow it down maybe too much.  I read an article that said my isp would see my virtual machine traffic if I use the host machine vpn.  Is this correct?  Thanks for any help.

---

### Post by howefield on 2022-02-08
Thread moved to the "*Windows*" forum.

---

### Post by #&amp;thj^% on 2022-02-08
When you have a VM under the Host, the VM can or may be configured to use Host&#8217;s Virtual VPN Network. Typically a VM will have to be configured to specify which host network adapter to use. In this case you will have to specify you are using the VPN Virtual Adapter. In this case the VM, will have the only option to ride on the VPN network. This is independent of what kind of networking you have chosen on your VM configuration such as Bridged, Host-only, etc. Of course choosing Internal network or choosing Bridged, Host-only riding on the default Ethernet gateway may not help establish a VPN on your VM. Some VPN connections may force all traffic on all networks now be re-routed via it&#8217;s virtual adapter. In that case **_not_** everything I said above will be true.
Another Thread was started here: [https://ubuntuforums.org/showthread.php?t=2471501&p=14080141#post14080141](https://ubuntuforums.org/showthread.php?t=2471501&p=14080141#post14080141)
You may find something useful there.

---

### Post by h4lman on 2022-02-08
Thanks for the link.  I'm new to this but its good to start learning the terms.

I've run tests from my Unbuntu virtual machine to sites like whatismyip and they all show my windows host vpn IP.  No dns leaks.  So I think it is working correctly.  I guess what I read about my traffic being exposed to my ISP with this setup must be incorrect.  I use a paid vpn service similar to Mulvad Wireguard and I did not make any adjustments when I set up the virtual machine.  I left it default install settings.

I'll just stick to this setup unless I'm missing something.  It sounds like adding a 2nd vpn inside the VM is doable with maybe a loss of 1/3 download speed.

---

