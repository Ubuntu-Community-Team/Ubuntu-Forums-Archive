---
title: "Ubuntu 20.04 VM Network Connection Suddenly Lost"
date: 2020-07-16
forum: Server Platforms
---

### Post by rebornjumpman on 2020-07-16
Greetings all,

My boss asked me to spin up a new ZoneMinder server and this is my first go at any kind of server (Linux or otherwise).  It's running Ubuntu Server 20.04 on a VMWare instance.  It was running find for about a week when suddenly the VM became unreachable except through VMWare's web console.  Unable to ping it from my machine I went to see if I could apt install a package and it gave me a resolution error.  I also tried to ping the router, DNS servers, and a few different websites but there is no connectivity with any of them.  I'm fairly new to this and am unsure of where to go from here.  Any help would be greatly appreciated.

---

### Post by LHammonds on 2020-07-16
If you have multiple hosts, try doing a vMotion migration to another host.  I have seen the NIC freak out before and only moving it from one host to another helped.  Rebooting or shutting down did nothing.

If you have no other hosts...dang, no redundancy...in that case, shut it down, edit the config and change the adapter from what it is using to something else (like Netx to E1000).

However, if you used the live installer that has the cloud-init package, you might have edited the network card settings in the wrong place and upon the 1st reboot, you lost the config.

LHammonds

---

