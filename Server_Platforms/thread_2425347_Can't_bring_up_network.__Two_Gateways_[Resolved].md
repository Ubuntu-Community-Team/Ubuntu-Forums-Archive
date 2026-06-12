---
title: "Can't bring up network.  Two Gateways [Resolved]"
date: 2019-08-24
forum: Server Platforms
---

### Post by waterwheel3 on 2019-08-24
Two gateways [Resolved]
Resolution - can't have two gateways.  Removed the second gateway, both machines came right online.

I'm just installing my first ubuntu server 18 machine, and simply cannot get the network online.  I fear a typo, but both myself and my IT guy have looked at this file for two days and cannot get it to work.
Here's the file in /etc/netplan:
```
# This file is generated from information provided by# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
 ethernets:
  eno1:
   dhcp4: no
   addresses: [XXX.XXX.XXX/29]
   gateway4: XXX.XXX.XXX.XXX
   nameservers:
    addresses: [8.8.8.8,8.8.4.4]
  eno2:
   dhcp4: no
   addresses: [10.0.22.3/24]
   gateway4: 10.0.22.1
   nameservers:
    addresses: [8.8.8.8,8.8.4.4]
  enp1s0:
   dhcp4: true
 version: 2

```

Symptoms:
- the 10.0.22.3 address works just fine.
- I can ping the external gateway for eno1
- I can't access anything past the gateway.
- nothing outside the gateway can access the machine.
- devices within the range of our switch can hit the external IP.  i.e. I have two machines like the above (both with the same problem) and I can access the external IP of each of them from the other machine (but again, not from the outside).  
- I deleted all the spaces and then carefully used the spacebar to reset the indentation, hopefully to remove that as a source of error.

I've tried everything including frowning at the monitor, to no avail.  Pretty sure it's either really stupid, or really complex :).  Thank you for any suggestions.

---

### Post by darkod on 2019-08-24
First a silly question. Is the public IP you are trying to assign yours? I am asking because I have sen cases where people simply disregard the recommendation to use private IPs and go for configuring public IPs that are owned by others.

Also, I would avoid using two gateways. If the eno1 is the primary interface and communications to the internet, use a gateway on it. On eno2 don't use a gateway. The server will still be able to communicate with the 10.0.22.0/24 subnet, it doesn't need a gateway for it.

I understand the need to hide public IPs in the post but know that this way no one can calculate if you maybe have wrong IP configuration. I have seen cases where people miscalculate.

When nothing outside the public gateway can acces both machines (but they talk to each other), maybe the issue is the gateway itself? Can anything outside the gateway communicate to anything inside it?

---

### Post by darkod on 2019-08-24
Taking a second look, try this:

1. In the yaml file add this:
```
network:
  version: 2
  renderer: networkd
  ethernets:
.....
```

Also, for eno1 addresses in your post you have only three octets ( XXX.XXX.XXX/29 ). Is that a typo in the post? Because it has to have four octets in the value.

---

### Post by The Cog on 2019-08-24
I agree with darkod about not having two default gateways configured. Which one would it use? Maybe it is trying to contact the internet via the internal 10.0.22.1 gateway.
The command **ip route** may prove that point.

---

### Post by aljames2 on 2019-08-24
As I recall, netplan is sensitive to spacing.  Be sure indentions are 2 spaces, not 1.  Notice this as darkod demonstrates in his suggested edit.

---

### Post by waterwheel3 on 2019-08-24
Thank you for all your help.  
The resolution was to delete the second gateway (the 10.0.22.1, internal gateway).  We removed that, restarted the network and everything came online immediately.

---

