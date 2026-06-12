---
title: "Xen guest DHCP issue"
date: 2013-03-01
forum: Virtualisation
---

### Post by philm1983 on 2013-03-01
Hi,

I have an Ubuntu 12.04.2 server running Xen hypervisor with 2 guests running.

1st guest is a Windows Server 2008 R2 server running DHCP & DNS services.

2nd guest is a Debian squeeze server with just a basic install.

Both are connected to the same bridge on the host which is then connected to eth0 on the host for network access.

The problem I am having is that the Debian guest will not get a DHCP address from the Windows guest running on the same host.  I know that the Windows server is giving out DHCP addresses to other devices external to the Ubuntu host, but the Debian guest will not receive an address.

If I manually set an address to the Debian guest I can ping external to the host and also to the Windows server guest so networking seems to be ok.  If I run a Windows server VM on a different host (running Virtualbox) then the Debian guest will get an address.  

I have also tried with an Ubuntu guest on the same host but this also does not receive an address.  

It's quite a strange one, it seems network traffic is passing through ok except for DHCP.

Phil.

---

