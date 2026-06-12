---
title: "Windows in virtualbox giving IP conflict..."
date: 2008-09-15
forum: Virtualisation
---

### Post by Ikith on 2008-09-15
TO explain my situation I am using parprouted to bridge my wlan to a virtual machine. This isn't working well! Its getting into the network which is obvious by the IP conflict errors but I cannot get them to go away. This is the script I'm using:

sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u username
ip link set tap0 up
ip addr add 192.168.1.198/24 dev tap0
parprouted eth1 tap0

It is working better than before where it wouldn't even give me an error but with a few corrections it has started picking up the ip conflict.

When asking windows to give itself an address (dhcp off tap which obviously wouldn't work) it gives 169 which is telltale that there is no dhcp which is true. So I give windows 192.168.1.198 and it picks up the conflict as it should. So this being said what addy do I give windows?

Edit: Just tried this script with same results
#/bin/bash
#wifibridge.sh
chown root:vboxusers /dev/net/tun
tunctl -t tap0 -u username
ip link set tap0 up
ip addr add 192.168.2.30 dev tap0
echo 1 > /proc/sys/net/ipv4/ip_forward
parprouted eth1 tap0

---

