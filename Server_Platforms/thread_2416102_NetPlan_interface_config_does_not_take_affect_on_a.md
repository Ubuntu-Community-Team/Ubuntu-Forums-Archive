---
title: "NetPlan interface config does not take affect on apply (requires reboot)"
date: 2019-04-05
forum: Server Platforms
---

### Post by ahhorner on 2019-04-05
Hi there, new to the forums so apologies if I do something wrong here,

I have installed Ubuntu Server 18.04 LTS onto a server which has two  NICs giving a total of 4 gigabit network interfaces. All 4 interfaces  are recognised by Ubuntu fine.

I removed cloud-init as it interfered with NetPlan and also the system  hostname, and then I created a new network config which works fine for  all of my interfaces.

My problem is that I will be using the interfaces with different  networks, as I will be using them for network testing. When I modify the  NetPlan config and do a generate and apply, the changes do not take  effect until the system is rebooted. An example of this is when I turn  off DHCP for one of the interfaces, which does not take effect and the  interface still receives an IP address via DHCP even after NetPlan  config has been generated and applied (both when applied whilst  interfaces are connected and applied whilst all interfaces have been  disconnected from any network).

Is there any way I can use NetPlan to apply my network configuration  live, or will I need to reinstall ifupdown and use that instead?

Thanks!

---

### Post by houstonbofh on 2019-04-07
I am not seeing a lot of good information on this.  I suspect it may be something they are "working on" as it is still new.  So I would fall back to the old tools.

---

