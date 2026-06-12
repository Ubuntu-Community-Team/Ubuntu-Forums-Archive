---
title: "networking problems with two nics"
date: 2009-07-24
forum: Server Platforms
---

### Post by Jago6060 on 2009-07-24
Ubuntu Server 9.04
3 connections available, only using the two on board, not the added nic.

Background:  Running Ubuntu Server as a host for a virtual machine(using vmware server 2).  The virtual machine is CentOS 5 with Project-Open installed.  Initially, this was running through a home linksys router(P.S. I did NOT set up this network).  We have since gotten a new switch and I have a sneaking suspicion that it doesn't allow multiple mac addresses on a single port.  I'm not sure if the mac address is an issue.  I believe the virtual machine will just use the eth0 which Ubuntu is using.

What I'm trying to do:  I want to tell the host to run traffic through eth0, and tell the virtual machine to run traffic through eth1.  Is this possible?

Here are some files that may help in your analysis.

---

### Post by koenn on 2009-07-24
> **Jago6060 said:**
> I have a sneaking suspicion that it doesn't allow multiple mac addresses on a single port.  I'm not sure if the mac address is an issue.  I believe the virtual machine will just use the eth0 which Ubuntu is using.
the virtual nic in the virtual machine wil have its own MAC addr.
however, I think it's unlikely that a switch would not handle multiple addresses on a single port : if you uplink a switch to another switch, the first switch will know that frames for devices on the 2nd switch will all have to go through that 1 port - all switches I've seen so far do that without thinking twice about it. 

> **Jago6060 said:**
> I want to tell the host to run traffic through eth0, and tell the virtual machine to run traffic through eth1.  Is this possible?

iirc, you can configure a virtual NIC to bridge to a specific physical nic on the host system. So this should be easy.

---

### Post by Jago6060 on 2009-07-25
> **koenn said:**
> the virtual nic in the virtual machine wil have its own MAC addr.
however, I think it's unlikely that a switch would not handle multiple addresses on a single port : if you uplink a switch to another switch, the first switch will know that frames for devices on the 2nd switch will all have to go through that 1 port - all switches I've seen so far do that without thinking twice about it. 


iirc, you can configure a virtual NIC to bridge to a specific physical nic on the host system. So this should be easy.


The reason I thought maybe it was a mac address issue was because of a post on the VMware forums.  Just something that triggered a "maybe" thought.  The way the setup was running before was...

Host: Static IP with default mac
  |
  ------>Virtual Machine: Static IP with mac assigned by the software

With this setup it was working fine.  Then we started using the new switch and everything went haywire.  Right now I can reach the host from another machine on the switch, but not the virtual machine.  Just to throw it out there, but the host is using the onboard Lan1 connection(eth1) and the VM is configured to use eth0.  But the software sets up the VM to use a bridged connection so it'll just share whatever connection the host is using.  Do you think the host using eth1 and the VM using eth0 is the issue?  So in other words, do you think there would be an issue if the VM was trying to bridge its own eth0 to eth1 on the host?

Additional Info:  Host-Ubuntu Server 9.04 64-bit, Guest OS(virtual machine)-CentOS5

EDIT: I tried to get iirc via "apt-get install iirc" but it couldn't find the package.  I'm not sure that iirc is the way I'm going to go, but it's definitely something I want to look into

---

### Post by koenn on 2009-07-25
> **Jago6060 said:**
> 
EDIT: I tried to get iirc via "apt-get install iirc" but it couldn't find the package.  I'm not sure that iirc is the way I'm going to go, but it's definitely something I want to look into
iirc - should have written IIRC: short for 'If I recall correctly'
:)

---

### Post by Jago6060 on 2009-07-25
> **koenn said:**
> iirc - should have written IIRC: short for 'If I recall correctly'
:)

Oh...epic fail by me :-P  Thanks for the clarification.  While we're indirectly on the topic of acronyms, is there a program that will help bridge the virtual nic to a physical one?  Or is that left up to the virtual machine software?

Currently I can add a connection to the virtual machine, but I can't really do anything with them.  They're just labeled as Network1 and Network2.  There isn't anywhere to define "go to ${eth} with mac address ${mac}".

---

### Post by koenn on 2009-07-25
> **Jago6060 said:**
>   Right now I can reach the host from another machine on the switch, but not the virtual machine.  Just to throw it out there, but the host is using the onboard Lan1 connection(eth1) and the VM is configured to use eth0.  But the software sets up the VM to use a bridged connection so it'll just share whatever connection the host is using.  Do you think the host using eth1 and the VM using eth0 is the issue?  So in other words, do you think there would be an issue if the VM was trying to bridge its own eth0 to eth1 on the host?

eth0 and eth1 are just symbolic names, they don't really matter. What matters is the device they refer to.

I don't have a VMware server available here to check (upgrade gone bad, no time to fix yet), but IIRC you should be able to chose in the VM's settings which physical NIC you want to map it to. Of course, this physical NIC will need to have a cable going to the switch. Of you plan to use one of the host's nics for the host itself, and the other nic to be used by the VM, you'll have 2 cables going to the switch, right ? Is that your problem ?

---

### Post by Jago6060 on 2009-07-25
> **koenn said:**
> eth0 and eth1 are just symbolic names, they don't really matter. What matters is the device they refer to.

I don't have a VMware server available here to check (upgrade gone bad, no time to fix yet), but IIRC you should be able to chose in the VM's settings which physical NIC you want to map it to. Of course, this physical NIC will need to have a cable going to the switch. Of you plan to use one of the host's nics for the host itself, and the other nic to be used by the VM, you'll have 2 cables going to the switch, right ? Is that your problem ?

Ok.  I have a question in reference to your first statement.  How do you change which nic eth0 and eth1 correspond to?  I'd like to disable all but LAN1, and have everything running through that one connection for simplicity.  The reason I ask is because I had the "interfaces" file setup with one entry for eth0 and a cable plugged into the LAN1 connection.  It wouldn't work.  So I changed the entry in the "interfaces" file to eth1, and it worked with the cable still in LAN1.

The software I'm using is VMware Server 2, which isn't quite as user friendly as VMware workstation.  I just double checked and unfortunately, there isn't any way to set the network connection to use a specific nic.  The only available options are to set the type of connection.  It's using a bridged connection, which should allow the VM to act as though its an actual computer on the network.  Alas...no luck...

---

### Post by koenn on 2009-07-25
> **Jago6060 said:**
> Ok.  I have a question in reference to your first statement.  How do you change which nic eth0 and eth1 correspond to?  I'd like to disable all but LAN1, and have everything running through that one connection for simplicity.  The reason I ask is because I had the "interfaces" file setup with one entry for eth0 and a cable plugged into the LAN1 connection.  It wouldn't work.  So I changed the entry in the "interfaces" file to eth1, and it worked with the cable still in LAN1.
you can probably get away with just ifconfig, something like
```

ifconfig eth0 down
ifconfig eth1 down

ifconfig eth0 hw ether 00:D0:09:DE:D4:6F up 

```
probably works with a static config. 
if not, you may have to look at /etc/udev/rules.d/70-persistent-net.rules for something like 
```
SUBSYSTEM=="net",DRIVERS=="?*",ATTRS{address}=="00:50:04:03:b9:4c", NAME="eth0"

```
but I have to admit I may be a bit out of date with this hardware recognition stuff

If your BIOS supports it, you might also try disabling one of the onboard network adapters.


> **Jago6060 said:**
> The software I'm using is VMware Server 2, which isn't quite as user friendly as VMware workstation.  I just double checked and unfortunately, there isn't any way to set the network connection to use a specific nic.  The only available options are to set the type of connection.  It's using a bridged connection, which should allow the VM to act as though its an actual computer on the network.  Alas...no luck...
Hm, yeah, and you cant set up virtual switches to work around that the way you'd do in ESX, I guess. Too bad.

---

