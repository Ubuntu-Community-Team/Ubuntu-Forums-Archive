---
title: "Client not finding Edubuntu DHCP Server"
date: 2008-07-02
forum: Server Platforms
---

### Post by grrrshn on 2008-07-02
Hello!  Just a quick note to thank everyone here for all you do to help the Ubuntu community!

I have an Edubuntu server up and running and working.  When I boot an IBM A31 Laptop PXE boot find the server just fine.  However I am now working on a second client in my house and having issues.

Initially the NIC would just pause on boot and give the following information:

Intel UNDI, PXE-2.0 build 082
SiS 900 PXE Boot Rom v1.03 Hook Int 18
Client MAC 00 D0 09 EA D8 4C GUID FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF

Upon further research research I discover the BIOS was out of date and flashing the BIOS would heal the Integrated NIC.  After the flash I get the following:

Novell Netware Ready Firmware v 1.00 (940809)
Copyright 1991-1994 Novel, Inc. All Rights Reserved
SiS 900/7016 PCI Adapters DOS ODI Driver v 1.10
Copyright 1998 SiS Corp All Rights Reserved

RPL-ROM-ADR:  00D0 09EA D84C
RPL-ROM-IRQ: 11
RPL:ROM-PIO: D40D

RPL-ROM-FCC: This counts from 1 to 5 after is states cannot find boot image and boots to the HDD.

Here is a copy of my /etc/ltsp/dhcpd.conf file
authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.3;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#   option routers 192.168.1.3;
#   option-ip-forwarding off;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
        host MGR {
           hardware ethernet 00:D0:09:EA:D8:4C;

What do I need to do to get the client to conenct to the Edubuntu dhcp server?

Thanks

Doug

---

### Post by promodus on 2008-07-03
I'm not sure what you mean by connect.

If you're talking about simply assigning addresses I think your configuration should do it.

However you're specifying a static mapping:
```
host MGR {
hardware ethernet 00:D0:09:EA:D8:4C;
```

And I don't see a closing }. I don't know what address is being sent to this host.

If you're looking to boot this client over the network, You'll need 
```
next-server ip.add.rree.ss;
filename "pxelinux.0";
```
And a PXE boot image, in most cases this is pxelinux, but there are many different files you can boot with.

---

### Post by grrrshn on 2008-07-04
Thank you promodus  I found a different NIC with PXE and worked well!

---

