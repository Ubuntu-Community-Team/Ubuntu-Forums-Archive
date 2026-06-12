---
title: "Virtualbox Networking Trouble"
date: 2020-02-19
forum: Virtualisation
---

### Post by Steve_Corenflos on 2020-02-19
Host: OSX (10.14.6)
Guest: Ubuntu Server 19.10 (64-bit)
VirtualBox: 6.1.2 r135662

Trying to get my host to be able to connect via web browser to a service running on my guest. I've been messing with this for a while and I'm getting frustrated. I've tried a dozen different permutations of instructions. I can't seem to get the two to talk to each other, not even so much as a ping. I am able to ping the DHCP server address from the guest, but that's it. While it seems as though the virtualbox DHCP server is running, it will not give out IP addresses and in the VirtualBox UI it gives an error if I try to tick "Configure Adapter Automatically."

At present I've tried setting a static IP on the guest to 192.168.56.101 (which would be the same IP the DHCP would have theoretically given me). I don't really care if it's DHCP or static in the end. I just want to be able to open a browser on the host and go to a web application on the guest, and I want no traffic from the internet to get to my guest.

Can someone help me figure this out?

I'm attaching the outputs of vboxmanage dhcpservers/hostonlyifs/natnets as well as ifconfig for the host and guest.

Thanks for any help!

---

### Post by SeijiSensei on 2020-02-19
If you use NAT for the VM guest's networking, and use DHCP on the guest, it and the host will have addresses in a 10 subnet.  Then you should be able to connect to the host using its 10 address.

Is the VM running a firewall?

[https://www.virtualbox.org/manual/ch06.html#networkingmodes](https://www.virtualbox.org/manual/ch06.html#networkingmodes)

---

