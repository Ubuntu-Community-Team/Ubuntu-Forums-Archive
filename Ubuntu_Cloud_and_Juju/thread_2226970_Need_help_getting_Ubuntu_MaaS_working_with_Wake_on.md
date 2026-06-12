---
title: "Need help getting Ubuntu MaaS working with Wake on Lan"
date: 2014-05-29
forum: Ubuntu Cloud and Juju
---

### Post by redDragon128 on 2014-05-29
Hello,
So far I've successfully commissioned 2 machines with MaaS through PXE Lan Boot, but I can't seem to get Wake On Lan working. I've been turning the machines on manually so far wherever MaaS would have attempted to WoL them.

Current setup:
1 Router
3 machines - 1 as MaaS server 2 as nodes
All 3 machines are connected to the router through normal LAN ports. Uplink is connected to internet

MaaS server is set up to do DHCP
[ATTACH=CONFIG]253590[/ATTACH]

Router is set to do DHCP as well but in a different range
[ATTACH=CONFIG]253592[/ATTACH]
WOL is enabled in Router
[ATTACH=CONFIG]253591[/ATTACH]

Odd thing is i can wake up both machines from the MaaS server or from my macbook using "wakeonlan" from command line. The server just doesn't do it when I hit commission or start or anything like that. I did have it working at one point but I don't know what combination of settings i had.

When I do turn it on manually though the machines are able to get the proper DHCP and PXE boot rom from the MaaS server. No matter what I do I just can't WOL them from MaaS.
Thanks for your help!

---

