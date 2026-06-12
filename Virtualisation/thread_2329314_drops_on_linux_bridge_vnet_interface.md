---
title: "drops on linux bridge vnet interface"
date: 2016-06-30
forum: Virtualisation
---

### Post by ceasiabaka on 2016-06-30
Are there useful tips or suggestions to understand what are causing drops on vnet interfaces of a KVM guest instance and what i can do to resolve/mitigate these drops.  
I am seeing these drops on a receiving end of a packet transmission. Source is a KVM guest on a different host with same spec as the receiving host.
No packet drops are seen on the vnet interface sending the packets as well as the bridge ports of it's KVM host. Also no drops are seen on the uplink bridge ports and bridge of the receiving host. 

Thanks

---

### Post by MAFoElffen on 2016-07-01
So you have a birdge on your KVM host ... and VM Guests.

Its this a public IP or local net?

Could you post the /etc/network/interface file please (within code tags). Note if it has a public IP, please edit the NID to host section of the IP, so it keeps your privacy (the world does not need to see it). Neither do I, if I know it has been edited.

What is the Guest OS and it's net settings?

What is the guests job and what resources do you have allocated to it as a guest?

No-one has answered you, so lets see if we can get you going again.

---

