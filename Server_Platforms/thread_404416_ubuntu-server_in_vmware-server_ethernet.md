---
title: "ubuntu-server in vmware-server: ethernet"
date: 2007-04-08
forum: Server Platforms
---

### Post by jmvidalvia on 2007-04-08
My host is Xubuntu.Edgy.
I installed vmware and XP as guest: first I choosed Bridged eth0, and it worked fine.
Later I wanted to share a directory and a printer using Samba: I learned that I had to select NAT instead of Bridged, in vmware-eth0 configuration. I also had to change some settings in XP lan configuration. Everything worked fine.
Then, I installed ubuntu-server as guest. It works, but I can not get internet working. I also want to share files using nfs and ssh betwen the host and the guest, as if they were two different machines in my lan.
I need help on how to configure that!
Thanks you very much.

PS: I enclose a png with vmware options.

---

### Post by Brazen on 2007-04-08
What makes you think you need to do NAT in order to share files and directory.  It would be much easier leaving it as bridged, and then you can share the files with physical computers on your network, too.

I believe if you go to the Ubuntu server documentation, they have good beginner info on ssh and nfs.

---

### Post by jmvidalvia on 2007-04-08
OK!
I leave it as "bridged".
How should I configure /etc/network/interfaces ?
Which interface is the system going to use? lo, eth0, eth1?
Thanks a lot!

Solved:
I added in /etc/network/interfaces:

auto eth1
iface eth1 inet dhcp

Thanks!

---

