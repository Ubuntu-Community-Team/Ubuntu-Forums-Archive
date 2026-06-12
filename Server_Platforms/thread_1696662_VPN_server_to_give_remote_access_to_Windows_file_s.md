---
title: "VPN server to give remote access to Windows file shares and printers"
date: 2011-02-27
forum: Server Platforms
---

### Post by jasbur on 2011-02-27
I am trying to set a VPN server using Ubuntu 10.10 to give remote access to local Windows resources. It would look something like this:

[Windows VPN client]-------->[Internet]--------->[Router]--------->[Ubuntu running pptpd]--------->[Internal Windows network with print servers, shared folders, etc]

As mentioned above I'm running pptpd on the Ubuntu machine. I can actually connect to the pptpd server on Ubuntu just fine, even connecting through the internet. However once connected I can't get access to any internal resource. I can't even ping any of the internal Windows computers. I can ping any Windows computer from the Ubuntu machine itself though. I also noticed I can't even ping google from the VPN client while connected.

This is the first VPN I'm setting up, so I may be going about this all the wrong way. Again, the intent is to use the Ubuntu machine to link a remote Windows VPN client into a local network so it can get access to local Windows file shares, etc.

Any advise would be appreciated.

---

### Post by Vegan on 2011-02-27
any servers besides the linux one?

---

### Post by cjhabs on 2011-02-27
A couple of comments:
When you are connected to the vpn all traffic is routed through it, so the only way you can get to the internet would be over the vpn - and that is not working - and will likely be slow once it does. I believe there are ways to control the configuration of this routing, I am not familiar with it.

Your problem sounds like you do not have routing configured between the vpn interface and the internal network interface.

---

### Post by SeijiSensei on 2011-02-27
> **cjhabs said:**
> Your problem sounds like you do not have routing configured between the vpn interface and the internal network interface.

+1

Another problem might that IP routing is disabled in the kernel.  At a terminal prompt, run "cat /proc/sys/net/ipv4/ip_forward".  If that returns zero, then routing is disabled.  To fix this, edit (as root with sudo) the file /etc/sysctl.conf and follow the instructions you see there about IP forwarding.  Then reboot.

---

