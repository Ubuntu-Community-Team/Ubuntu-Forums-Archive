---
title: "Remote server by booting stuck on Ctrl+D message"
date: 2016-09-19
forum: Server Platforms
---

### Post by kamiware on 2016-09-19
Dears,

I have a server that is 1000 km away from me.
This morning it got rebooted, and right now I have nobody close to the server that can check it.

I can ping the server, but no services are online.
I have had this before, and it was because some issue with the ZFS [FONT=monospace]zpool[/FONT]. And someone had to press Ctrl+D, and then the server continues booting.
Afterwards the ZFS [FONT=monospace]zpool[/FONT] was not mounted, and I had to do "zpool import -f poolname" to get it mounted.

In any case, now I have 2 questions:

1) Is there some way for me to remotely force the server to continue booting, without the ZFS pool. (Right now I have no way to SSH into it, so basically, I need some way to take the console.

2) Can I change this for the future, so that the server in future will no longer hang on issues with the ZFS pool?

[edit]For infromation: I'm running Ubuntu 16.04. the main system is installed on an ext4 lvm partition. So I can boot up the server without the ZFS pool.[/edit]

Thanks,
Samuël

---

