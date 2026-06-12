---
title: "lxc fails to start container because zfs is not ready - Ubuntu 16.10"
date: 2016-12-19
forum: Virtualisation
---

### Post by cgtobi on 2016-12-19
Hi all,

[COLOR=#111111][FONT=Ubuntu]On my Ubuntu 16.10 server I have a bunch of lxc containers on top of zfs. Ever other boot of my server lxc fails to start containers due to missing zfs/zpool. When I reboot the system comes up fine. Apparently the order in which lxc and zfs are starting is not consistent. How can I make lxc depend on zfs being up and running the right way before messing things up?

Thanks in advance for any help or suggestions.

Cheers,
cgtobi[/FONT][/COLOR]

---

### Post by cgtobi on 2017-01-08
Hi all,

just a quick update. I was able to fix my problem by modifying the zfs systemd config file to require local disks beeing finished first. Now everything is running fine so far.

Cheers,
cgtobi

---

