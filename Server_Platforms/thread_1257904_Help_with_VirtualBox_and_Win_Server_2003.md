---
title: "Help with VirtualBox and Win Server 2003"
date: 2009-09-04
forum: Server Platforms
---

### Post by Dridhas on 2009-09-04
Hello,

  I just installed Windows Server 2003 on VirtualBox VM...

im using Ubuntu 8.10 and im trying to ping/connect to the VM but im unable to do it...

can you please help me out on this?

im a noob on this..

Thanks in advance!!! :D

---

### Post by Bachstelze on 2009-09-04
How is your network configured in VBox?

---

### Post by Dridhas on 2009-09-04
here are the configs that i have for the network in ubuntu and in Win Server 2003

**Ubuntu Config:**
ath0      Link encap:Ethernet  HWaddr 00:05:4e:4e:a4:51  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe4e:a451/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:249664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:364378619 (364.3 MB)  TX bytes:11103089 (11.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:11:25:46:59:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6996 (6.9 KB)  TX bytes:6996 (6.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-4E-A4-51-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289556 errors:0 dropped:0 overruns:0 frame:37647
          TX packets:146049 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:377901434 (377.9 MB)  TX bytes:15489507 (15.4 MB)
          Interrupt:11 


**Win Server 2003 Configs:**
Microsoft Windows [Version 5.2.3790]
(C) Copyright 1985-2003 Microsoft Corp.

C:\Documents and Settings\Administrator>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : server
   Primary Dns Suffix  . . . . . . . : casa.test.com
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : casa.test.com
                                       test.com

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapter
   Physical Address. . . . . . . . . : 19-02-16-08-01-10
   DHCP Enabled. . . . . . . . . . . : No
   IP Address. . . . . . . . . . . . : 192.168.1.10
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :



hope it helps...

thanks!!

---

### Post by Bachstelze on 2009-09-04
That's not what I was asking for. I meant how your network was connfigured in VBox, i.e. whether you're using NAT, bridged or host-only network(s).

---

### Post by Dridhas on 2009-09-04
Sorry, my mistake...

the Network options are: Attached to NAT

---

### Post by Bachstelze on 2009-09-04
> **Dridhas said:**
> Sorry, my mistake...

the Network options are: Attached to NAT

That's your problem. When configured in NAT mode, the VM cannot communicate with the host. You have two solutions: either replace your NAT interface with a Bridged one, which will give you both access to the Internet and to the host, or add a Host-only interface, which will let your VM communicate with the host, while the NAT one will take care of the Internet.

---

### Post by deeq on 2009-09-04
> **HymnToLife said:**
> That's your problem. When configured in NAT mode, the VM cannot communicate with the host. You have two solutions: either replace your NAT interface with a Bridged one, which will give you both access to the Internet and to the host, or add a Host-only interface, which will let your VM communicate with the host, while the NAT one will take care of the Internet.

Or you can port forwarding your NAT.

Host terminal:
```

VBoxManage setextradata "vm name" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/GuestPort" 80
VBoxManage setextradata "vm name" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/HostPort" 8080
VBoxManage setextradata "vm name" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/Protocol" TCP

```

---

### Post by Dridhas on 2009-09-04
ok, i changed the option to Bridged Adapter and now i can ping either way (from host to guest and viceversa)...

The only thing now is that i do not have internet access from the guest...

any ideas on how to fix this?

Thanks in advance!!

---

### Post by Totalknowledge on 2009-09-04
It looks like you need to set up your gateway.

---

### Post by Dridhas on 2009-09-04
ive no idea what i did, but somehow the connection to and from the guest is working as well as the internet...

thanks a lot!!

---

### Post by Bachstelze on 2009-09-04
> **Dridhas said:**
> ok, i changed the option to Bridged Adapter and now i can ping either way (from host to guest and viceversa)...

The only thing now is that i do not have internet access from the guest...

any ideas on how to fix this?

Thanks in advance!!

If you set your interface to Bridged, you need to configure networking on your VM just like you would if you connected another real machine to your router (from your router's point of view, the VM will just be another computer).

---

