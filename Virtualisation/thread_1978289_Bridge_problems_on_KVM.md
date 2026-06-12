---
title: "Bridge problems on KVM"
date: 2012-05-11
forum: Virtualisation
---

### Post by gerger09 on 2012-05-11
I've configured the bridge using this guide [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) but when I connect using eth0 the host loses connection to the network. The guest machine takes all the connection. How do I configure it in a way that they both have a connection but it's still on bridge mode?

---

### Post by cmont899 on 2012-05-11
Please post the contents of your /etc/network/interfaces

---

### Post by gerger09 on 2012-05-11
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

# The bridge network interface, used by kvm
auto br0
iface br0 inet dhcp
	bridge_ports eth0
	bridge_stp off
	bridge_fd 0
	bridge_maxwait 0

---

### Post by cmont899 on 2012-05-11
> **gerger09 said:**
> when I connect using eth0 the host loses connection to the network.

Based on your interface file eth0 is not getting an IP, how are you connecting to the host over eth0?

---

### Post by gerger09 on 2012-05-11
Through LAN. I tried setting it on dhcp instead of manual but I still get the same result. For now I removed the bridge so I can connect to the internet using LAN.

---

### Post by gerger09 on 2012-05-12
I can access the router's web management interface when connected to the LAN but I am unable to access the Internet when in bridge mode. I've been trying to solve this problem for a month now.

---

### Post by Dedoimedo on 2012-05-13
What kind of network connection is eth0? Wired/wireless?
Dedoimedo

---

### Post by gerger09 on 2012-05-13
eth0 is wired

---

### Post by houstonbofh on 2012-06-13
Your interfaces file looks good.  Did you install the cap net admin and assign the users correctly? [https://help.ubuntu.com/community/KVM/Networking#Assign_CAP_NET_ADMIN_Capability](https://help.ubuntu.com/community/KVM/Networking#Assign_CAP_NET_ADMIN_Capability)

I am thinking this may be your issue.

And did you see the last line at the bottom of [https://help.ubuntu.com/community/KVM/Networking#Creating_a_network_bridge_on_the_host](https://help.ubuntu.com/community/KVM/Networking#Creating_a_network_bridge_on_the_host)
> If your VM host "freezes" for a few seconds after starting or stopping a KVM guest when using bridged networking, it is because a Linux bridge will take the hardware address of the lowest numbered interface out of all of the connected interface. To work around this, add the following to your bridge configuration:

post-up ip link set br0 address f4:6d:04:08:f1:5f

and replace f4:6d:04:08:f1:5f with the hardware address of a physical ethernet adapter which will always be part of the bridge. 

If this does not help, post the results of "ifconfig" in a shell.

---

### Post by Dedoimedo on 2012-06-15
What does your route look like - route -n.
Dedoimedo

---

### Post by gerger09 on 2012-06-17
I gave up so I used macvtap instead which works great.

---

