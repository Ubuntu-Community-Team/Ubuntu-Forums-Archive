---
title: "Bridge - Waiting for network configuration"
date: 2012-10-14
forum: Server Platforms
---

### Post by Swirfin on 2012-10-14
Hello guys.

I'm having some boot trouble with my ubuntu server 12.04 LTS. Just to start things of, I'm pretty new to ubuntu and linux, so please be patient.

During boot I get "Waiting for network configuration". Then it waits 60 more seconds for network configuration, finally it boots without actually getting the interfaces up.

After logging in, I simply do a
```
sudo ifdown eth0
sudo ifup eth0
```And everything works perfectly.

Here is my /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.137
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
auto br0
iface br0 inet static
address 192.168.1.137
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports eth0 eth1
```I have found that commenting out the lines related to the bridge removes the problem.

I have also found that there is a big difference between turning of the computer completely, and rebooting it. Maybe it has something to do with bringing up the physical interface? (i.e. rebooting with bridge works, powering up with bridge doesn't work)

I have read through numerous launchpad bugs that are showing the same symptoms that I'm having, but I haven't found the solution.

I have no spanning-tree functions or anything like that implemented on the network. 

Is there something wrong with my bridge configuration? Should there be some kind of fault-handling in the configuration that I haven't implemented?

---

### Post by darkod on 2012-10-14
What are you actually trying to achieve? Bridging from eth0 to eth1 and vice versa, or simply some kind of bonding (link agregation)?

---

### Post by Swirfin on 2012-10-14
> **darkod said:**
> What are you actually trying to achieve? Bridging from eth0 to eth1 and vice versa, or simply some kind of bonding (link agregation)?
I have one cable going from my router to the room where my printer and server is. In order to have both of them connected to the network I found it easier to bridge the network interfaces on the server rather than buying a switch or pulling another cable through. So basically the bridge just extends the network onto another segment.

---

### Post by darkod on 2012-10-14
According to this, it should be easy but it's done differently from how you did it:
[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

Note that at the top it says it's for 12.04 and it doesn't mention installing the bridge-utils package that the earlier versions seem to need.

This is for 10.04 and it does mention installing bridge-utils, also the config in /etc/network/interfaces is slightly different:
[https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html)

Bridging is mentioned at the end.

---

