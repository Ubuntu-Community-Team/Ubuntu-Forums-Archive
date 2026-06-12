---
title: "Network in XP guest no longer works"
date: 2013-10-15
forum: Virtualisation
---

### Post by ofnuts on 2013-10-15
It used to work... and it stopped working, but I cannot relate this to a kernel or a VBox update. Basically, the network on the XP guest doesn't work.

Host: Kubuntu 12.10
Guest: XP SP3
VirtualBox: 4.2.18 (Oracle edition, not the open-source one)

The guest was created a long while ago under Kubuntu 10.04 using the Virtual Box OSE from the distro. When I upgraded to Kubuntu 12.10, I move to the Oracle version of VB, but this worked without problems for several months... (with a caveat: when logging on it can take a while before the desktop appears, without any disk/CPU activity on the guest, and I have always suspected network problems there). 
 
The Guest has a NAT network adapter, without any port forwarding. From the VB perspective, all is OK (cable is connected, and address assigned (10.0.2.15).

On the guest, the interface seem to be defined correctly (and the MAC address displayed above matches the one in the VBox config):

```

Windows IP Configuration

        Host Name . . . . . . . . . . . . : VBOX-XP
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapter
        Physical Address. . . . . . . . . : 08-00-27-B3-01-CB
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.0.2.15
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.2.2
        DHCP Server . . . . . . . . . . . : 10.0.2.2
        DNS Servers . . . . . . . . . . . : 10.0.2.3
        Lease Obtained. . . . . . . . . . : 15 October 2013 13:06:09
        Lease Expires . . . . . . . . . . : 16 October 2013 13:06:09

```

The routing also looks OK:
```

===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...08 00 27 b3 01 cb ...... AMD PCNET Family PCI Ethernet Adapter - Determin
istic Network Enhancer Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0         10.0.2.2       10.0.2.15       20
         10.0.2.0    255.255.255.0        10.0.2.15       10.0.2.15       20
        10.0.2.15  255.255.255.255        127.0.0.1       127.0.0.1       20
   10.255.255.255  255.255.255.255        10.0.2.15       10.0.2.15       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
        224.0.0.0        240.0.0.0        10.0.2.15       10.0.2.15       20
  255.255.255.255  255.255.255.255        10.0.2.15       10.0.2.15       1
Default Gateway:          10.0.2.2
===========================================================================
Persistent Routes:
  None

```

But, from the guest:
[LIST]
[*]I can ping the host on 10.0.2.2 
[*]I can ping the guest itself on its loopback interface (127.0.0.1) 
[*]I cannot ping the guest itself on its LAN interface (10.0.2.15) 
[*]I cannot ping the DNS server on on 10.0.2.3 
[/LIST]

And tracert... wait a minute, while I'm typing this, the whole thing starts working again (although I still cannot ping 10.0.2.15 and 10.0.2.3)(some minutes before, tracert would display "no route to host")

This is driving me... nuts. Sometimes I would prefer a good and permanent failure to this elusive problem that is taking a lot of my time. Of course it cannot be a hardware problem :) 

Any ideas of things to check?

---

### Post by ofnuts on 2013-10-17
Curiouser and curiouser.... It seems that the problem occurs when an application in the guest is trying to use something else than the port 80 or 443 (and unfortunately I do have to connect to servers with special HTTP ports). As far as I can test, once the TC/IP link is set up (which means I can reset the whole thing by virtually unplugging-replugging the cable in the VB control panels), if the first connection uses something else than 80 or 443 the guest networks locks up. If I un-replug the cable, ping the host, and then start using the other ports, it works.  I once suspected a firewall in the guest but the problem still occurs after it has been disabled.

Not sure that anyone will answer to this, so this is posted just in case someone with the same troubles is directed to the post above.

---

