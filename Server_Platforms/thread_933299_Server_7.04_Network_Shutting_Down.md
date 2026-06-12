---
title: "Server 7.04 Network Shutting Down"
date: 2008-09-29
forum: Server Platforms
---

### Post by dweimer on 2008-09-29
I am trying to test the Possibility of using Ubuntu server 7.04 x64 as a Squid Proxy server running on a VMware ESX 3.5 Server.  The install went fine, installed Squid from Source configured it and testing is going fine with one problem.  When ever the server is idle for a while I can no longer access it from the network, until I log into the console, and access something on the network from it.
Its likely that when this system is rolled out that it will never have enough down time for this to occur, however I can't consider it a successful test with this problem.  I have been searching for LAN power saving information, but I have not been able to find any information on how to query what is set, or disable it.
I do have the VMWare tools installed, the problem did exist before installing them as well, was hoping they would fix the problem.

---

### Post by alastair on 2008-09-29
Could be a VMware issue really.

Why don't you install the current (LTS) release Hardy 8.04?

Alastair

---

### Post by dweimer on 2008-09-29
OK, the reason I didn't was I apparently looked at an old version of the VMWare ESX guest OS Install guide, and it listed 7.04 as the latest supported version of Ubuntu server.  After seeing this reply I double checked and as of 3.5 U2 the 8.04 LTS is supported, I will make this change and see if the problem goes away.

---

