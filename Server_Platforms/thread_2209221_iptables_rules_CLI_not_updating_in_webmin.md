---
title: "iptables rules CLI not updating in webmin"
date: 2014-03-04
forum: Server Platforms
---

### Post by cylent on 2014-03-04
i am trying to use webmin to configure my iptables however sometimes i type commands in via the CLI.

Well when i do that in webmin it doesnt update.

its as if things are not synchronized ... why is this and how do i save commands entered in via CLI then update them to show in webmin?

---

### Post by darksideforge on 2014-03-04
Updating the IP tables via CLI are temporary, aren't they? To make permanent changes, don't you have to vi or nano into /etc to set/save variables (hence the need/usefulness of Webmin to begin with)? Here's what's got me thinking that:

> IP Addressing
The following section describes the process of configuring your systems IP address and default gateway needed for communicating on a local area network and the Internet.

Temporary IP Address Assignment

For temporary network configurations, you can use standard commands such as ip, ifconfig and route, which are also found on most other GNU/Linux operating systems. These commands allow you to configure settings which take effect immediately, however they are not persistent and will be lost after a reboot.

To temporarily configure an IP address, you can use the ifconfig command in the following manner. Just modify the IP address and subnet mask to match your network requirements.

```
sudo ifconfig eth0 10.0.0.100 netmask 255.255.255.0
```

[HTML]https://help.ubuntu.com/12.10/serverguide/network-configuration.html[/HTML]

Hope that helps. ~dsf

---

