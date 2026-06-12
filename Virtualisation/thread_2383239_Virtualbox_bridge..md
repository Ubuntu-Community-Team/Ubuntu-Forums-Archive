---
title: "Virtualbox bridge."
date: 2018-01-22
forum: Virtualisation
---

### Post by jeff.sadowski on 2018-01-22
I use virtualbox at home on my fedora 27 server and bridging to the local interface I have no issues.

I use Ubuntu 16.04 at work and have been trying to bridge the guest OS to eno1 network interface but I am having no luck. I can't seem to find a working solution.

I tried setting promiscuous mode on the interface and on in virtualbox.
I still can not get an ip from my networks dhcp server.
It seems something is preventing my user from using the interface to get an ip for the guest OS.

I tried creating a bridge interface by adding

auto br0
iface br0 inet dhcp
   bridge_ports eno1
   bridge_stp off
   bridge_fd 0
   bridge_maxwait 0

to /etc/network/interfaces
and restarting networking via

/etc/init.d/networking restart

then I tried creating tun0 via
ip tuntap add tun0 mode tap user myusername

then as soon as I run the following my machine  stalls and I have no alternative to hard powering off and on again

ip link set tun0 master br0

# lspci|grep Ether
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)

It seems networking on ubuntu is broken horribly.

I am using active directory users in ubuntu via samba I'm not sure how that would make a difference.
I was going to try fedora 27 in a vm to see if I can start using it with the same smb.conf I use to join my ubuntu and centos here at work but I am fighting with virtualbox on ubuntu 16.04

So my questions are:

What would be preventing my user from setting up a bridge to the eno1 interface? Is there a way to allow my users

Am I doing something wrong when I try to bridge tun0?

---

### Post by wildmanne39 on 2018-01-22
*Thread moved to **Virtualisation, a more appropriate forum**.*

---

### Post by jeff.sadowski on 2018-01-22
I'm not sure that is a more appropriate forum for this. This has way more to do with networking in ubuntu than virtualization.

---

### Post by wildmanne39 on 2018-01-22
I a sure you it is the proper place and you should receive more help in this forum then in networking.

---

### Post by jeff.sadowski on 2018-01-22
OK, thank you.

More things I have tried.

I removed my br0 and went back to trying bridging directly from virtualbox.

I added my user to the following groups:
root, adm, sudo, netdev, vboxusers, libvirtd

Still no luck bridging to eno1

---

### Post by jeff.sadowski on 2018-03-13
I had gone to Fedora 27 and bridging works in Fedora but I still could not get my VM to obtain a dhcp address until I found what the problem was. It had nothing to do with linux at all. My issue was port security on my cisco switches. After allowing the mac on my vm on my cisco switch I could get my vm under fedora to get an IP.
I suspect Ubuntu would have worked as well. So this is mostly fixed. That I could not work with bridges in ubuntu I'm going to stay away from Ubuntu.

---

