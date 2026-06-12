---
title: "Network interfaces in Hyper-V"
date: 2011-01-21
forum: Server Platforms
---

### Post by MangoPapaya on 2011-01-21
Hi
I installed Server 10.10 (2.6.35-22-server #33-Ubuntu SMP Sun Sep 19 20:48:58 UTC 2010 x86_64 GNU/Linux) on Hyperv-R2. IT went smooth and syntetic adapter were up and running after configuring them in /etc/network/interfaces.
The problem is that sometimes, after a reboot or a crash, the network interfaces change name. The kernel logs
[ 5.850928] udev[430]: renamed network interface eth0 to eth4
So i have to modify config to have it work again.
I have Windows and FreeBSD machines that run with no problems. Any idea to solve the issue?
Thanks

---

