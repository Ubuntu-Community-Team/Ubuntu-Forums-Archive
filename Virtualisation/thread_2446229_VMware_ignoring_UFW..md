---
title: "VMware ignoring UFW."
date: 2020-06-26
forum: Virtualisation
---

### Post by tremain on 2020-06-26
I am running VMware Workstation Pro 15.5.2 on Ubuntu 20.04 with Gufw turn on. PC traffic is restricted to only use Tun0 and all applications and services are correctly refused outbound connection without VPN connection. Recently I discovered that any VM machine using 'Bridged Network Connection', with or without 'Replicate Physical Network Connection State' turned on/off, completely bypasses UFW using the non-VPN connection. All VMware VMs function correctly with VMware NAT and only communicate via Tun0 and VPN with NAT, but when switched to 'Bridged' it again bypasses the VPN and ignores the rules for Tun0. With the app 'Advanced Network Configuration', the 'Automatically Connect to VPN' is turned on with a selected VPN connection. How do I force a bridged virtual network adapter to use Tun0 and be blocked by UFW?

Background: I connect remotely through a gateway forwarded port to ssh into a CentOS VM when reading/studying Linux on the road. This isn't a major issue but I have concerns about the VM being directly exposed across the ssh port (changed to non-standard port) to the Internet where it could be sniffed. It appears that VMware's bridged port feature is literally creating a second, nested network connection, completely ignoring all ufw rules and completely bypassing the vpn and Tun0. I am surprised that interface bridging completely ignores ufw and creates it's own private connection out of the protected network. Thanks.

---

### Post by TheFu on 2020-06-26
i think that is working as designed.  Treat the VM just like you would a physical host.  Setup VPN, tunnel, firewalls, etc.

Be certain to secure the ssh connection.  [https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by tremain on 2020-06-29
Thanks. Not what I expected but I understand it and see how it could be an advantage.

---

