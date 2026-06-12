---
title: "Dapper+VLANs+HTTPS=Problems?"
date: 2006-09-13
forum: Server Platforms
---

### Post by tbcpp on 2006-09-13
Okay, here is the problem. This past week we re-designed our network here at work to look like the following:


Internet
|
|
Router/Firewall (Using Static IP)
|
Vlan 6
|
DMZ
|
Main Routers (actually two)
|
Client VLAN, Server VLAN, Misc VLANs


Our main routers have 5 ethernet ports on them. All the systems mentioned above (the routers and the firewall) are running Ubuntu Dapper Server. Since we wanted to be able to expand later, we tried to use vlans as much as possible. Hence we defined the vlans via vconfig in Linux. So the router would use ethernet port eth0.6 to talk to the main routers.

After installation we started noticing some really odd problems. First of all, our 98 clients joined the network fine, got their logon scripts and ran them. However, our XP machines did not. After a bit of head banging my co-worker and I modified it so that the routers used eth1, eth2, eth3, etc. Instead of eth1.11 or eth1.21. Then we set our HP switch to do the tagging. It worked like a charm.

However, on one of our other nets all HTTPS traffic stopped working. Just a few minutes ago I set the main firewall to use eth1 instead of eth1.6 and let the switch do the tagging and it's working great.

What on earth is going on here? Is there some limitation on VLANs that I don't know about? The freaky thing is, the HTTPS traffic is still being tagged by the main routers for vlan 21! So instead of being tagged by linux, routed and tagged by linux again, they are being tagged by the hp switch the seccond time.

Any ideas? On all occations we could ping, and "see" the hosts. Its just some traffic wouldn't work. And it's not an iptables issue because when we changed the ethernet devices it worked without modification to the iptables.

I'm stumped.

---

### Post by drakkan on 2006-09-13
Vlan in linux works well if you have high quality ethernet cards with good linux driver, for me intel nic (driver e100 and e1000) works fine.

What ethernet card are you using?

---

