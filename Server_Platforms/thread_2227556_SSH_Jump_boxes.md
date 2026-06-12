---
title: "SSH Jump boxes"
date: 2014-06-02
forum: Server Platforms
---

### Post by dangad999 on 2014-06-02
Hi All,

I have a small issue with SSH. Basically we use ssh to connect to all our servers in different application environments (all Ubuntu 12.04 servers) and each environment may have servers in other locations (not on the same network -> and may require another ssh "jump".

Can I can use proxyCommands which use the remote servers' /etc/ssh/ssh_config file to run the next hop in the chain?

I can successfully run ssh host1 -t ssh host2 which calls the remote /etc/ssh/ssh_config but as soon as I add this my local ~/.ssh/config on my workstation I get all kinds of stdout errors.

Does anyone have a solution?

PS  - I know about and use the tried and tested proxycommand nc solution in other areas of the network but I dont think netcat will provide the functionality I need for this issue.(I think).

Thanks

---

