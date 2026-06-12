---
title: "optimal /etc/sysctl.conf values"
date: 2014-02-21
forum: Server Platforms
---

### Post by sebastiaopburnay on 2014-02-21
Hi!

I have a 64bit Ubuntu Server 12.0.4 LTS in a VMware ESXi farm and I'm using it as a Nagios' central monitoring node.

The machine has 4vCPUs and 3GB of RAM

My machine has to passively receive thousands of TCP connections with remote probe statuses and then it writes them to a third party MySQL Database.
[IMG]https://dl.dropboxusercontent.com/u/4311557/Drawing6.jpg[/IMG]
I'm having capacity issues handling all these I/O interactions and I've seen posts suggesting to increase some values in /etc/sysctl.conf 

I tried values suggested in some forum, but they must have been too high to my VM's resources. So high, the machine literally freezed and dI had to force reboot it via VCenter.

So, in order for the machine to function, I wonder how high can I set the values:
[LIST]
[*]kernel.msgmnb
[*]kernel.msgmax
[*]kernel.shmmax
[*]kernel.shmall
[*]kernel.msgmni
[/LIST]

Thank you in advance for your time and shared know-how.

Best regards,
Sebastião

---

### Post by sebastiaopburnay on 2014-03-10
The diagnostics and actions in an [external forum post ]("http://support.nagios.com/forum/viewtopic.php?f=7&t=25587&start=10")proved this to be related to kernell values configured in /etc/sysctl.conf.

Apparently, the default values on this Ubuntu Server x64 12.04 LTS were not enough for an ndomod.o instance, in the central Nagios' host for the troughput (and process/thread footprint) produced by +- 350 hosts with 2200 services scheduled with 5min intervals.

In the post mentioned you can find the appropriate values that enabled an allways fresh NDOUtils remote database.

Thank you, the post can now be locked/solved

---

