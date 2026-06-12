---
title: "LXC Bridged Networking on Same Network as Host - Help"
date: 2013-03-25
forum: Virtualisation
---

### Post by jeff808 on 2013-03-25
Running 12.04.2 LTS.
I can ping out from/connect ssh into the host but can't ping anywhere except to the host from my container.
I can ping to the container from the host but not from anywhere else.
I want the container to have an address on the same network as the host.
The container somehow gets a DHCP lease. Not sure how.
I've set things up thusly:
The name of the container is "spam" (this will be a test container for some spamassassin stuff)

Host networking config:
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0

/var/lib/lxc/spam/config config (networking part):
lxc.network.type=veth
lxc.network.link=br0
lxc.network.flags=up
lxc.network.hwaddr = 00:16:3e:13:c1:a0
lxc.utsname = spam

Container networking config:
auto eth0
iface eth0 inet dhcp

Host's NIC is set to promisc mode on.

Set net.ipv4.ip_forward=1 in /etc/sysctl.conf (don't now if this was necessary, but someone somewhere said it was).

Set USE_LXC_BRIDGE="false" in /etc/default just to take that out of the picture and use my own br0.

Based on what I've seen online, this should get things working the way I want. Is there anything I'm missing that's preventing it from working? I've found lots of old stuff from previous builds of LXC, but it looks like the 12.04 and 12.10 builds are supposed to make things much easier, so I'm not sure what info is relevant from the older tutorials.

Thank you.

---

### Post by jeff808 on 2013-03-26
Bump...

Would really like some help with this since I want to get LXC going. Maybe it should've gone in the networking section...?

---

