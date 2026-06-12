---
title: "XEN with OpenVswitch bridges"
date: 2013-11-04
forum: Virtualisation
---

### Post by 3f846a38d004f5251e on 2013-11-04
Hello,

I`m using XEN 4.3 with openVswitch 1.11.0 as network birdges.
My physical netzwrok interface (eth0) is a 1 Gbit network card.
When I communicate with other clients in the real LAN from my VMs,
the network speed is 1 Gbit. This is OK.
Then I created a new XEN openVswitch bridge with only the VM network interfaces without eth0.
I thougt the speed will be at least 10Gbit, between the VMs on the XEN host, but I only have 1 Gbit.
I can rate the speed down with the commands,
ovs-vsctl set Interface win_172-emu ingress_policing_rate=60000
ovs-vsctl set Interface win_172 ingress_policing_rate=60000
but the maximum speed is 1 Gbit. 
Is it possible to speed up the OVS Xen bridge to e.g. 10 Gbit for internal VM ethernet communication ?

best regards
B.-D.

---

### Post by romihs on 2014-02-26
Hello,

I am also interested in this, and I am sad to see that there are no replies to your question.

I have a XEN setup with a file-server serving up iSCSI volumes to VM's and I would love to get 10Gbit throughput, or at least better than 1Gb...

Have you found a way to exceed the 1Gb barrier?

BR
SR

---

