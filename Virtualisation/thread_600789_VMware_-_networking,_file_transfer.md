---
title: "VMware - networking, file transfer"
date: 2007-11-02
forum: Virtualisation
---

### Post by abhiroopb on 2007-11-02
I just installed VMWare. The main reason I installed it was because I urgently needed to run Adobe InDesign and although I have a dual-boot with windows I thought that having a virtual machine would make life easier. 

Anyway I have the following problems:

1. Networking:

When I was asked (during installation) which networking card I wanted to use (eth0 or eht1) I picked eth1 as that was my wireless card (I found this after right clicking on my wireless icon and clicking on connection information. Upon running VMware I am getting the limited or no connectivity sign. The connection type is set to bridged. Although I have a decent knowledge of networking I don't really know what bridged, NAT, and the rest mean. 

Our cable modem is connected to a wireless router which is picked up by my wireless card, so what should I do to enable internet on the virtual space?

2. File transfer

Quite simply how do I transfer files between my Ubuntu with my virtual Windows. Currently if I drag and drop I get the following error "Unable to open: Virtual machine "/home/xxxx/test.doc" is not in the inventory."

Help appreciated.

Regards,

Abhiroop

---

### Post by Delvien on 2007-11-04
> **abhiroopb said:**
> I just installed VMWare. The main reason I installed it was because I urgently needed to run Adobe InDesign and although I have a dual-boot with windows I thought that having a virtual machine would make life easier. 

Anyway I have the following problems:

1. Networking:

When I was asked (during installation) which networking card I wanted to use (eth0 or eht1) I picked eth1 as that was my wireless card (I found this after right clicking on my wireless icon and clicking on connection information. Upon running VMware I am getting the limited or no connectivity sign. The connection type is set to bridged. Although I have a decent knowledge of networking I don't really know what bridged, NAT, and the rest mean. 

Our cable modem is connected to a wireless router which is picked up by my wireless card, so what should I do to enable internet on the virtual space?

2. File transfer

Quite simply how do I transfer files between my Ubuntu with my virtual Windows. Currently if I drag and drop I get the following error "Unable to open: Virtual machine "/home/xxxx/test.doc" is not in the inventory."

Help appreciated.

Regards,

Abhiroop

For networking to windows from ubuntu or vice versa, check out Samba, you can find quite a few how-to's on the forums here.

As far as networking, I would personally use NAT networking, it gives the VM a good connection straight to the network and gives the VM a route-able IP address (in case you wanted to terminal in ) Works great for me.

NAT = Straight connection to the network, gives the VM its own IP address like its a physical computer sitting on your desk

Bridged= Shares IP address and networking with the Host.

to reconfigure your settings do the following:

```
 /usr/bin/vmware-config.pl 
```

---

### Post by koenn on 2007-11-04
> **Delvien said:**
> As far as networking, I would personally use NAT networking, it gives the VM a good connection straight to the network and gives the VM a route-able IP address (in case you wanted to terminal in ) Works great for me.

NAT = Straight connection to the network, gives the VM its own IP address like its a physical computer sitting on your desk

Bridged= Shares IP address and networking with the Host.


I think you got it backwards : 

"BRIDGED" --> The Virtual NIC uses the physical NIC of the Host to connect to the physical network. The VMachine gets its own IP address etc and therefore multiple 'guest" systems can be bridged. The VMachines then appear as (physical) hosts on the LAN - allowing you to use all the usual networking protocols : SSH, Samba, ...  
Network infrastructure (eg DHCP, ...) must be provided by the physical network.

HOST Virtual Adapter : creates a (virtual) network adapter on the HOST through which the HOST system has network connectivity to the Guest system. Can be used for
		- communication (eg filesharing, ssh, ..) between host and guest
		- connect the guest to the ouside world through NAT + routing

Problem with NAT would be that it's one-way : connections initiated by the guest system will work, but connections from outside towards the guest system won't work (so no "ssh in to it") because NAT isn't transparant to inbound connections.

---

### Post by abhiroopb on 2007-11-05
In case anyone is interested:

For networking I set it to NAT and it worked without any problems

For file transfer I used the following guide [[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+how-to]](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+how-to]) and set up a samba share which is very effective.

BUT, I found vmware VERY slow it made the windows VM slow as well as the host ubuntu. So, I tried out virtualbox (with similar settings, NAT, and samba) and it works almost seamlessly.

---

### Post by nsilva on 2008-06-16
Keep in mind that you do not need to re-compile it through the installation script mentioned above. You can change the network configuration inside VMWare

---

