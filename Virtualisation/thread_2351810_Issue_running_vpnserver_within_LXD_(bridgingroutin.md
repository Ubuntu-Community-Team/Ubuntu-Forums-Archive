---
title: "Issue running vpnserver within LXD (bridging/routing within the guest itself)"
date: 2017-02-07
forum: Virtualisation
---

### Post by itcrowdsource on 2017-02-07
Hello,

I’ve been struggling setting up a vpn server within an LXD guest. In my case I’m using Softether.
Tried several options to allow remote clients to my network. E.g. bridging or routed. But I’m stuck. 
I’ve managed to setup the same vpn software succesfully on KVM but I can’t get it working on LXD. (So I know how to configure the server properly)
The guest VM is able to access all other hosts on the internal network so connectivity is OK.

First of all I’m unable to create a L2 bridge interface because it doesn’t recognize a compatible nic. If I setup a NAT based routed connection it doesn’t route packets outside the guest VM host itself.

I suspect this is all related to the LXD network stack.

Does anybody have any suggestions to fix this? Could this be related to the restricted mode of the containers? Not sure where to start…
Hope anyone has tackled this before. Probably such issues also arise with other vpn/networking products.

Robert

---

### Post by itcrowdsource on 2017-02-13
Problem solved, it appeared to be a low-level setting in Softether. Changed a setting from```
 bool DisableIpRawModeSecureNAT false
``` to ```
bool DisableIpRawModeSecureNAT true
```
LXC/LXD seems to have a problem handling this NAT mode.

---

