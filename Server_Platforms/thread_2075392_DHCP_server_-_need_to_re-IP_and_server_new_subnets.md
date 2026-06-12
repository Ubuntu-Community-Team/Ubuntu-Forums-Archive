---
title: "DHCP server - need to re-IP and server new subnets"
date: 2012-10-23
forum: Server Platforms
---

### Post by BakCompat on 2012-10-23
Ok, so I have a DHCP server sitting on an ancient box. I want to replace it but don't have an available box yet. So, I have this server serving DHCP for 4 different subnets... 114.0, 115.0, 126.0, & 127.0 currently assigned x.x.114.2

We are moving to an entirely new IP range and I already have DNS migrated to a new box, but need to get the DHCP off of the existing subnets and start serving the new subnets. So, if 100+ clients are connected with their respective dhcp IPs across 4 subnets, do I just edit the dhcpd.conf file and remove all instances of existing subnets and add the new subnets in and follow that up with changing the IP of the server to the new IP and apply the changes?

I want the existing leases to time out, and upon request for new IP, be assigned an IP in the range of the new subnets.. x.x.50.x, x.x.51.x, x.x.52.x, x.x.53.x

---

### Post by darkod on 2012-10-23
I don't understand what's the problem. Simply turn off (delete) the old dhcp ranges and create the new ones. From that moment on, the dhcp server will start to offer them.

What you need to be careful with is to have the old gateway and dns servers still available until all old leases expire.

If you also plan to move the gateway to now IP, that would cause the clients to have valid lease for X more time, but no valid gateway/dns, etc.

If you have the old and new gateway and dns online at the same time, no sweat. Simply activate the new ranges and let the old leases expire.

---

### Post by BakCompat on 2012-10-24
Yes, I want to just move all new leases to the new range of IPs.. 

Existing server sits at A.B.4.2 serving DHCP to A.B.4.65-254

whereby I want it to become X.Y.50.2 serving DHCP to X.Y.50.64-254, 51, 52, and 53 subnets..

My understanding is that dhcpd can only serve IPs out in the range it sits on.. So.. can I just add a secondary IP of X.Y.50.2 on eth0:0 and add the new subnets and delete the old ones? Once all leases are moved over, I would then re-IP the box permanently to X.Y.50.2 and remove any instances of it's original A.B.4.2 and related info

---

### Post by darkod on 2012-10-24
I am not sure how assigning a second IP goes. Or whether you can assign interface like eth0:0 to the dhcp server.

Just today I tried something similar with a VLAN interface eth0.100 and it failed. It might have been some other error on my part though.

---

### Post by BakCompat on 2012-10-24
I went ahead and did it. I added a virtual IP to the DHCP server on eth0:0 and restarted the network and verified it was reachable publicly. Then is removed the old subnets in dhcpd.conf and added the new subnets under a shared network. Applied the changes and now I'm seeing the slow addition of new IPs in the pools according to the new subnet range.

Prior to adding the secondary IP, I was unable to serve the new subnets out.

---

