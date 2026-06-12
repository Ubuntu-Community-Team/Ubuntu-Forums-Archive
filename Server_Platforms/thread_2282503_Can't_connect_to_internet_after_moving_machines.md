---
title: "Can't connect to internet after moving machines"
date: 2015-06-14
forum: Server Platforms
---

### Post by 215xed on 2015-06-14
I  have 4 Ubuntu servers currently 1 ftp and 3 web servers. I moved them from one room to the room across the hallway. Before I moved them they worked and connect online just fine with no issues. Once moved connecting online seems to not be happening. The ftp server when directly connected to the modem seems to work fine but no connection through the switch. I directly connect the web servers to the modem with no luck. All 4 machines connect through a switch normally which as always worked fine. LAN port lights are on and working on each machine, command ifconfig shows they are connected and broadcasting. Each machine is set with a static ip address. Router admin settings does not show them as connected devices. I have tried diff cat cables, bought a new switch and no luck. All I can think of is the router/modem is not recognizing the static ip for some reason. Which I am not sure how to fix. ATT U-verse Pace modem/router. Modem recognizes desktop running Mint 17 and desktop Peppermint with static and the ftp server with static but not the 3 web servers direct connected or through the switch... Can anyone point me in the right directions to solve this super annoying problem

---

### Post by volkswagner on 2015-06-14
This is likely misconfigured network config. Please post /etc/network/interfaces file. Are these CLI only aka no desktop environment with network manager installed?

I'd start by changing one machine to DHCP instead of static, will also help confirm if it's a config issue.

Can you ping the router's IP from the server?

---

### Post by TheFu on 2015-06-15
Do some troubleshooting.
Please post the results (copy/paste) for each command, in order:
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

