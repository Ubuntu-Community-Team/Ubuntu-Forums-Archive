---
title: "Problem with hosting server on Ubuntu Guest"
date: 2011-02-20
forum: Virtualisation
---

### Post by gtirtha on 2011-02-20
Hi,

I have Ubuntu 10.04 as guest on Windows XP host.
NAT has been created to use internet in guest OS (ubuntu).
My topology is like my PC is connected to a router which has internet input.
Now, I want to host a server on Ubuntu, say tftp server. So, I added another Bridged adapter to VB.
With this I got another network interface with router class IP in Ubuntu.

Now, if I connect another PC with router and try pinging my guest Ubuntu, it works but unable to do tftp transfer. Always timeout is happening.

I have tried, VBoxManage setextradata in Windows XP to forward guest port 69 to host port 69 and then trying connecting XP machine for tftp, without any success.

Please advice me what would be easiest way to achieve a TFTP server on VirtualBox Ubuntu guest on Host XP.
Thanks in advanced.

---

