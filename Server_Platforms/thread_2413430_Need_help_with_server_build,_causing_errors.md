---
title: "Need help with server build, causing errors"
date: 2019-02-25
forum: Server Platforms
---

### Post by alschmitt44 on 2019-02-25
[COLOR=#242729][FONT=Arial][FONT=inherit]Thanks for taking the time to read and comment. Essentially a noob here trying to get this working.[/FONT]
[FONT=inherit]So I am attempting to put together a home media server on Ubuntu 18.04. I have done this in a VM on a windows machine, but a recently built a new gaming rig, and am repurposing the old one into a server. Here is my plan, and then the problems. This is on baremetal fyi.
[/FONT]
[FONT=inherit]I have a 128gb ssd acting as / and /home at /dev/sda. On here I have used [https://github.com/GhostWriters/DockSTARTer](https://github.com/GhostWriters/DockSTARTer)[/FONT]
[FONT=inherit]to get containers up and running. Everything works well for a day or two, until Radarr, Sonarr, or other containers begin to give me ERR_CONNECTION_REFUSED. I am trying to make sense of this and believe it to be because docker has dynamic dns, but I am not very familiar with networking. I did not have this problem when running in a VM, which was running in windows with bridged adapter on oracle Virtualbox. My thoughts on getting around this was going to a hypervisor and was considering proxmox.
[/FONT]
[FONT=inherit]Issue two: I have four 8 tb drives in a Zfs RaidZ1. I have this mounted under tank, and used the default dockstarter app to point the data to the drive at /tank/medialibrary/movies and /tank/medialibrary/tv. I set these up in Radarr and Sonarr. It shows my 20.4 TB of storage, and appears to be sending the data there, but I just filled up my /home file on the /dev/sda last night. I am using transmissionvpn for torrents. I believe this must be a problem with the /dev/sda and Zpool not being able to share data. I have considered just making the boot drive into a Zpool, but some people don't seem to like that approach as ZFS is not standard in Linux.[/FONT]
[FONT=inherit]Any help and ideas of how to make this work are appreciated![/FONT]

[/FONT][/COLOR]

---

### Post by TheFu on 2019-02-25
I cannot help, sorry, but I can say that as a noob you've jumped into the deep end of the pool with many of the technologies you have selected.  I've only been a Linux admin since the early 1990s, so perhaps my thoughts aren't useful.  I've not been happy with containers, since to use them correctly, they really shouldn't have any local data or run anything except the single process intended. No shell, no ssh, nothing extra. To make updates/changes to a container means to rebuild it from a fresh stack build process.

ZFS is not suitable as boot or OS storage on Ubuntu at this point. That is clear.

Again, I'm sorry that I'm not any help.

---

