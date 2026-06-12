---
title: "Ubuntu Gutsy DomU network not working."
date: 2008-01-15
forum: Virtualisation
---

### Post by jdsw2002 on 2008-01-15
Hi
   I am mainly a Fedora user but I am trying to use
Xen on Ubuntu. I installed the ubuntu-server-xen
package. And my system is upto date. Also have
network-script to  network-bridge and vif-script to
vif-bridge. Added loop_max=64 to the /etc/modules.

Problem
=======
The  domU N/w is not working

the bridge does not seem to have any interfaces. On
Fedora it had peth0 and vif0.0. The Ubuntu
distribution is having veth0.. interfaces.

brctl show 
bridge name     bridge id               STP enabled   
 interfaces
xenbr0          8000.feffffffffff       no            
 

As I start the VMs the vif<domid>.0 interfaces do get
added. But the domU does not get the n/w (as I think
the other end of the bridge is not setup correctly).
This is true for both PV and HVM guests

I tried to add manually veth0, brctl fails with
invalid argument.
I tried adding vif0.0 and eth0. With this my domU n/w
worked but dom0 n/w is lost.!!

Any ideas on how to resolve this. 
See attachment with brctl output, ifconfig -a output and xm info output.

Thanks
/Jd

---

### Post by hurenkam on 2008-03-09
Hi,

Normally, in bridge mode, xen will move the mac & ip of eth0 to veth0, then rename eth0 to peth0 and add it to xenbr0. Then it will add vif0.0 to xenbr0 as well.

The bridge should at least contain the peth0 and vif0.0 devices, so that the guest machines are connected to the physical ethernet (you should then be able to ping outside machines).

For the guest to be able to connect to the host, you need to add an IP to the bridge (the network-bridge should do that automatically, but if it hasn't added vif0.0 then something is wrong anyway, so you can try to do that manually).

What the exact reason is for xen failing to properly setup xenbr0 is hard to tell from your post, but it could be that eth0 is not configured properly (or not existing, perhaps you connect through eth1 or eth2?) prior to startup.

Mark.

---

