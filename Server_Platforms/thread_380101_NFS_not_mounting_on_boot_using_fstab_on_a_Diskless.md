---
title: "NFS not mounting on boot using fstab on a Diskless setup"
date: 2007-03-09
forum: Server Platforms
---

### Post by tbaptista on 2007-03-09
Hi,

I've been stuck on an issue with a diskless setup. I've managed to resolve the issue and thought of sharing here in the forums.

I installed a diskless setup following this guide:
[https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto")

The server is using dapper (6.06.1 LTS) and the clients feisty (7.04).

Everything is working fine, except for the home directory that doesn't get mounted on boot, but if I try to do "mount -a" on the console, it works.

The problem was in the /etc/network/interfaces. The guide advises to comment out the auto eth0, as the interface is already up by the initramfs. That is correct. The problem is that the script /etc/network/if-up.d/mountnfs is only called on network up and not for the loopback interface. As I wasn't bringing any interface up, the nfs /home was never mounted on boot.

The fix is to define the interface as auto, but set it to manual config.
My /etc/network/interfaces for the client:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The eth0 interface is already configured by initramfs
auto eth0
iface eth0 inet manual
```

Hope this helps anyone with a similar problem.

--------------------------------------------------------
Tiago Baptista

---

### Post by afljafa on 2007-03-13
That explains some problems I had.

I simply added lines to rc.local

```
mount -tnfs -onolock 10.0.0.5:/mythtv/music /mythtv/music
```

---

