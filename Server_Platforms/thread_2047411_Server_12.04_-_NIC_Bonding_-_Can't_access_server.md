---
title: "Server 12.04 - NIC Bonding - Can't access server"
date: 2012-08-24
forum: Server Platforms
---

### Post by SBinVA on 2012-08-24
[SOLVED] - Apparently the 100MB link was the problem, due to sloppy punch work on the patch panel. Too bad I only have myself to blame for that. :-)


Ok, a fair n00b here, especially on the Server side of Linux.

I've bonded 5 NICs for LACP link aggregation based on this guide: [https://help.ubuntu.com/community/UbuntuBonding]("https://help.ubuntu.com/community/UbuntuBonding")

Everything looks OK (except one of the ports on the switch is showing a 100MB link on one of the nics... in case that's important)

The problem I'm having is that I can no longer access webmin or any of the existing samba shares from a windows machine, nor can I ping the server. 

ifconfig looks good, the switch shows all of the links as up, so I'm not sure where to go from here. 

Any help will be much appreciated.

Thanks,
SB

---

