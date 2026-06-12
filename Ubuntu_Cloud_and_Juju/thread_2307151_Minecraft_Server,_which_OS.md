---
title: "Minecraft Server, which OS?"
date: 2015-12-22
forum: Ubuntu Cloud and Juju
---

### Post by alexander59 on 2015-12-22
So... I'm starting a Minecraft server with an actual server (Dell PowerEdge 2850 w/ upgrades). It has plenty of processing and RAM power for it, and I was wondering, which operating system should I use? I tried to install MineOS, but it seemed to hate the idea of running off of a RAID configuration. I am now installing regular Ubuntu 14.04 LTS, and wanted to know if I should use a different OS?

Any help would be appreciated!

Alex

---

### Post by ian-weisser on 2015-12-22
If you want a headless server, Ubuntu Server 14.04 will provide a slightly superior experience.

Those tips will prevent most of the server-related help requests I see in this forum.:
1) Do not boot from RAID. Boot from a non-RAID device. The unnecessary extra complexity of RAID-during-boot has caused much regret and shed many tears.
2) Backup game data frequently (RAID is not a backup). 
3) Treat Minecraft like a service, and use Upstart to start/stop/restart it. Not your login shell, not a bunch of hacky scripts.
4) Use the proper permissions, owerships, and accounts. Don't run Minecraft as root. Don't run Minecraft as your login user.
5) Turn on automatic system upgrades, including autoremove.

Take notes on how to properly set it up. You will need those notes in 2018-2019, when you migrate the games over to 18.04 LTS.

---

