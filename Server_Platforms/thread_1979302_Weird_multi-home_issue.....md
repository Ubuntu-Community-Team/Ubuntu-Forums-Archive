---
title: "Weird multi-home issue...."
date: 2012-05-13
forum: Server Platforms
---

### Post by tonyric on 2012-05-13
I have two physical nics in a NAS box I built.... I have a switch that has been configured with two VLANs and this is working on my ESXi servers. But my NAS box will only communicate on one network and the config looks correct.... See below:

> 
root@pigpen:/export# netstat -anr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U         0 0          0 eth1
root@pigpen:/export# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:03:0c:7e
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe03:c7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72494422 errors:0 dropped:0 overruns:0 frame:39
          TX packets:6671445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:106679526386 (106.6 GB)  TX bytes:553000991 (553.0 MB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:1b:21:a0:b9:f5
          inet addr:192.168.100.20  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fea0:b9f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:114833 (114.8 KB)  TX bytes:5765 (5.7 KB)
          Interrupt:16 Memory:f0320000-f0340000



As you can see, I have no gw set up on the 192.168.100.xxx network (eth1), which is the private network for storage in my virtual environment. I cannot ping on eth1 anywhere on 192.168.100.xxx but eth0 works perfectly.

OK folks, I am not new to Linux (not even remotely) but WTH? LOL

EDIT to add: I am using ports that are properly configured for the appropriate VLAN.

---

### Post by elico on 2012-05-13
you can start with a tcpdump when pinging from another machine and if there is no traffic dumped can be a vlan issue.
if it indeed dumped you can get into the higher application levels such as firewall or others.

---

### Post by koenn on 2012-05-13
what elica says.

or
> EDIT to add: I am using ports that are properly configured for the appropriate VLAN.
Are you sure ? Did you verify that VLAN port conf is not an issue, by testing connectivity on eth1 in a no-vlan envoronment ?  or on untagged ports ?

---

### Post by tonyric on 2012-05-14
> **koenn said:**
> what elica says.

or

Are you sure ? Did you verify that VLAN port conf is not an issue, by testing connectivity on eth1 in a no-vlan envoronment ?  or on untagged ports ?

VLAN config is verified, also moved the nic to a port that is currently used by one of my esxi servers... The server is operational in the port previously used by the NAS box and the NAS box is inoperable in the ports previously used by the esxi server.

Watched the activity lights and it appears that traffic is still routed through eth0 when it should be going through eth1 for 192.168.100.xxx

Very odd

---

### Post by tonyric on 2012-05-14
> **tonyric said:**
> VLAN config is verified, also moved the nic to a port that is currently used by one of my esxi servers... The server is operational in the port previously used by the NAS box and the NAS box is inoperable in the ports previously used by the esxi server.

Watched the activity lights and it appears that traffic is still routed through eth0 when it should be going through eth1 for 192.168.100.xxx

Very odd

Also, no firewall on the NAS box.

---

### Post by hawkmage on 2012-05-14
As long as you are not needing/wanting to access any other subnets  connected to the 192.168.100.* through eth1 then not having a gateway is  no issue.  

How are you doing the VLANs?  Are you setting the default VLAN on the switch for the port or are you using VLANs on the Linux interface?  

What happens if you use the "-I' option to make ping use the eth1 interface?  This will determine if it is an issue with routing determining what interface to use or there is an issue with communicating on the VLAN.

---

### Post by koenn on 2012-05-14
> moved the nic to a port that is currently used by one of my esxi servers... The server is operational in the port previously used by the NAS box and the NAS box is inoperable in the ports previously used by the esxi server.
That's not conclusive.
If your esx nic and both switch ports are VLAN-"tagged" ( [http://en.wikipedia.org/wiki/IEEE_802.1Q](http://en.wikipedia.org/wiki/IEEE_802.1Q) ) but your NAS nic isn't, that's exactly the expected result, at least on the HP Procurve switches a use.  

That's the reason hawkmage's question is relevant.

What if you connect an other machine (a laptop, ...) -- with appropriate network config i.e. in the same subnet -- directly to the NAS, no switches involved. Can they ping each other ?

---

### Post by tonyric on 2012-05-15
I re-verified the port settings, ports 1-8 are tagged vlan id 1 which is used for 192.168.0.xxx and 9-16 for vlan 100 used by 192.168.100.xxx. All ports are tagged correctly, also all ports on both vlans are allowed to accept tagged and untagged frames. There is no tagging happening on the nas box, the ESXi boxes are tagged as that's the default config for vmware. I will enable tagging on the NAS box and see if that fixes the issue, will note this thread for others if it works.

NOTE: My vCenter server works as multi-homed (virtual machine), but this works of course because it is using the same physical nics as the ESXi servers on vlan 100 and both ESXi servers talk find on vlan 100 regardless of the port used that are configured for vlan 100. So, it looks like tagging is the issue.

---

### Post by hawkmage on 2012-05-15
I also run ESXi but I have 3 VLANs defined and trunked across 3 switches.  

Did you try the ping with the "-I" option to specify the eth1 interface to force it to use the proper interface?  

I assume that you are not using VLAN tagging on the Linux interface eth1 since normally a Debian VLAN interface is a virtual interface on top of a physical one and you would likely not be using the name eth1.  

Besides being a member of VLAN 100 are you having the switch tag untagged packets as VLAN 100 on ports 9-16?  If not the switch will treat untagged packets as VLAN 1.

---

### Post by tonyric on 2012-05-16
It was vlan tagging..... Simple fix:

apt-get install vlan
vi /etc/network/interfaces
change eth1 to eth1.100
Save file

modprobe vlan
ifup eth1.100

all works

add 8021q to /etc/modules

Thanks everyone for pointing me in the right direction.

---

