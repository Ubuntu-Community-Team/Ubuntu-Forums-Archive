---
title: "VirtualBox dhcp-server problem"
date: 2010-06-17
forum: Virtualisation
---

### Post by morgonhed on 2010-06-17
Hi,

I am trying to set up a dhcp-server for VirtualBox internal networking, however I always get an error:

```

 VBoxManage dhcpserver add --netname intnet --ip 192.168.0.1 --netmask 255.255.255.0 --lowerip 192.168.0.2 --upperip 192.168.0.5
Oracle VM VirtualBox Command Line Management Interface Version 3.2.4
(C) 2005-2010 Oracle Corporation
All rights reserved.

ERROR: code NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value (extended info not available)
Context: "CreateDHCPServer(NetName.mutableRaw(), svr.asOutParam())" at line 248 of file VBoxManageDHCPServer.cpp
error: failed to create server

```

Regardless of ip-range, network-name etc I always get this same error.

I have installed the latest VirtualBox via the deb as provided by Oracle.

Any ideas what I could try?

Many thanks!

---

### Post by TheFu on 2010-06-18
I've never used DHCP under vbox, so this is a shot in the dark.  If you have another DHCP server running on the same network, they can conflict.  Is the network/subnet that you are using above different from the network that your other machines use?
[FONT=monospace]
[/FONT]192.168.0.x is my concern. Perhaps 192.168.77.x addresses would be better for your DHCP clients?

---

### Post by morgonhed on 2010-06-18
> **TheFu said:**
>  If you have another DHCP server running on the same network, they can conflict. 


There is no other dhcp-server running. 
And it would not matter for the problem at hand.
The problem is not a conflict, but the fact that the VirtualBox dhcp-server is not even starting.

> **TheFu said:**
> 
192.168.0.x is my concern. Perhaps 192.168.77.x addresses would be better for your DHCP clients?

Why do you think that? In what respect would the 192.168.77.0 network be different?
And besides when using internal networking the "network" that VirtualBox creates is not even visible to the outside world (not even to the host), so you could use any address range you like.

But again the problem is the dhcp-server not even starting...

---

### Post by morgonhed on 2010-06-21
This issue has now been confirmed to be a bug which will be resolved in an upcoming release ([http://forums.virtualbox.org/viewtopic.php?f=7&t=32184](http://forums.virtualbox.org/viewtopic.php?f=7&t=32184)).

---

