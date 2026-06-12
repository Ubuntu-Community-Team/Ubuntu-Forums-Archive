---
title: "[netns] high cpu usage"
date: 2011-04-13
forum: Server Platforms
---

### Post by brav0 on 2011-04-13
Hi,
We just deployed a new storage-server running 10.04-server. 
After redirecting some traffic to the machine we started seeing a high cpu usage from a process called [netns]. I've done some googleing and it seems to be the Network Namespace kernel option (NET_NS). I'm not sure what it does, but I'm kind of frustrated with the high load that we aren't seeing on the other machines running gentoo.

Can someone please provide me with some information on:
What does this service do?
Why is it standard in the server-kernel?
Is there anything i can do about the load other than recompiling the kernel without the NET_NS option?

The machine is running nginx and vsftpd and serves many hundred requests per second.

---

### Post by brav0 on 2011-04-13
found possible info on this matter here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/720095](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/720095)

---

