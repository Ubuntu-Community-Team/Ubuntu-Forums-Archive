---
title: "Issues using tightvncserver in"
date: 2024-03-13
forum: Virtualisation
---

### Post by thomas_margotta on 2024-03-13
I'm running Ubuntu from os boxes in a virtual machine and can't figure out which IP address to use. It's all on the same internal network and theirs a VPN. Just trying to get a virtual machine for miscellaneous stuff to work remotely and team viewer thinks Im doing something commercial so im trying to get away from it. I tried the ipv4 address that's like 192.168.56.xxxx something or other. I enabled some other network cards to see if it helps but it isn't working. Does anyone have a tutorial or something?

---

### Post by TheFu on 2024-03-13
Step 1 - clearly outline the two computers, their EXACT IPs, which LANs they are on and how they must be connected.  Until you do that, nobody can help.

If the remote system uses a VPN and isn't on the same LAN, then you'll need to make a connection to their VPN first. That's completely unrelated to running a remote desktop.

If you use libvirt + virt-viewer/virt-manager for the remote system server, then remote desktop is built-in and goes over an ssh connection.  Don't do things the hard way, especially on the same LAN.  Why do people want to do things the hard way?  RDP and VNC are the hard way.

---

