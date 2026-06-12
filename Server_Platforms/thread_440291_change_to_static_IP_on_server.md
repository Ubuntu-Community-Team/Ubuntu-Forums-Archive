---
title: "change to static IP on server"
date: 2007-05-11
forum: Server Platforms
---

### Post by twinax on 2007-05-11
What is the best to change the IP address on a 7.04 server to Static

---

### Post by heimo on 2007-05-11
Edit /etc/network/interfaces. To see syntax:
```
man interfaces
```

For example:
```

auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0

```

---

### Post by Highway on 2007-05-30
> **heimo said:**
> Edit /etc/network/interfaces. To see syntax:
```
man interfaces
```

For example:
```

auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0

```

When i do the above to give my machine a static ip address, and then do:
invoke-rc.d networking restart

it takes ages.  Looking at my syslog, i can see it is broadcasting for a dhcp address, even though my interfaces files looks is as follows:
# The primary network interface
auto eth0
iface eth0 inet static
address 10.149.32.2
netmask 255.255.254.0
gateway 10.149.32.193

Do you have any idea why it is still looking for an address via dhcp.  When it eventually gives up, it has accepted the static address.  

Any ideas why this might be happening?
Highway

---

### Post by Highway on 2007-05-30
Ok, now it gets more strange.  When i was setting the static address above, the machine was not on the network.
When the networking eventually restarted, running ifconfig eth0 showed that the address in the interfaces file had been accepted.
Then, when i plugged in the network cable, it started broadcasting for dhcp again, and picked up a new address on my LAN and is now using that.
I have only one ethernet interface in this machine.

Can anyone shed any light on this behaviour.  

Highway.

---

### Post by MrHorus on 2007-05-31
> **Highway said:**
> 
Then, when i plugged in the network cable, it started broadcasting for dhcp again, and picked up a new address on my LAN and is now using that.
I have only one ethernet interface in this machine.

Can anyone shed any light on this behaviour.  

Highway.

Are you running dhclient?

Perhaps you might use iptables to block dhcp requests?

---

### Post by Highway on 2007-06-01
dhclient was installed as default, but i shouldn't need to block the requests with the firewall.  I would still have to wait ages for it to timeout, and anyway there should be no requests in the first place if it is using the interface file properly. 

Highway.

---

