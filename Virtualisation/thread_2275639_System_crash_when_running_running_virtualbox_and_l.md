---
title: "System crash when running running virtualbox and lxc (container)"
date: 2015-04-27
forum: Virtualisation
---

### Post by odror on 2015-04-27
US: Ubuntu 15.04 (gnome desktop)
Vbox : 4.26 64bit
CPU: i7-4770
RAM 24GB
HD: 500 GB evo850 SSD

After upgrading from 14.10 to 15.04 one of my applications (zoneminder 1.28.1) fail to run. I created an lxc container (ubuntu 14.10). It was running now in this container.

While the container was running the system crashed when booting any of my virtualbox clients (W7 or ubuntu 14.10). The vbox client did run when the container was not active.

I have read a thread from a couple of yeas ago about this issue. The idea behind virtualization is to isolate from the host machine. This is clearly an unintended consequence. I am "guessing" the the issue is because of the network bridge used by lxc and vbox. The lxc network bridge was on a separate (10.x.x.x) network than vbox, which was on 192.168.x.x. Both has static IP. The second one is also my home LAN. Both were also on a separate bridge interfaces to the same local interface (eth0). From what I have read if lxc is on NAT bridge. This issue does not exist. The documentation for lxc are sparse and incomplete. 

Did any one have this issue or have an idea how to fix it. Also is there a different networking setup that will avoid this issue. How do I set NAT bridge in lxc (v.s. the default setup)

After multiple crashes my system stopped booting. I was not able to recover even with boot-repair. I had to go back to the old SSD (14.10). That is another issue, where in 2015, the a live CD is not adequate for recovering a boot issue.

I would appreciate any help.

Thanks

---

