---
title: "[SOLVED] Ideas for a Ubuntu Virtual Machine"
date: 2007-07-21
forum: Server Platforms
---

### Post by illuniel on 2007-07-21
hey there Ubuntu Guru's

i had this idea where i would like to create an ubuntu virtual machine that acts as my server. I would like to have a 1 machine network solution.  In it, i would like to install the followingr:

PFsense, > a router/firewall  (heck, my linksys routers are not as good as this one!)
FreeNAS > file server

now, these things would load up when the Ubuntu Server fires up and there would be 3 NIC's on the machine. I would like to know if anyone here as accomplished this or anything similar.

*to my understanding also, the ubuntu server gui is a cli right? can vmware install and run on that?

---

### Post by jtc on 2007-07-21
> **illuniel said:**
> *to my understanding also, the ubuntu server gui is a cli right? can vmware install and run on that?

yes, yes

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by illuniel on 2007-07-21
absolute coolness :D 

can you configure and map the NIC ports to certain vmware virtual machines?  

for instance, 
eth0, eth1  >  PFsense
eth2 > FreeNAS

have you sucessfully done this? :-)

---

### Post by jtc on 2007-07-21
> **illuniel said:**
> 
can you configure and map the NIC ports to certain vmware virtual machines?  
...
have you sucessfully done this?

Yes, Yes.

---

### Post by illuniel on 2007-07-21
Hi again, wondering how to go about the following:

How do I use PFsense with this? 

do i use 2 Ethernet ports:
eth0, eth1 
how do i configure them?
both as bridged? 
will both show up in the vmware "Edit Virtual Machine Settings"?

Do i use 1 ethernet port and then have 2 virtual ports? how would that be configured if i have one as WAN and the other as LAN?

pls advise on this as I am trying this now. thanks! :confused:

---

### Post by jtc on 2007-07-21
I have no experience with PFsence.

On the vmware-side you want to configure them all as bridged.

When it comes to edit the virtual machine you can access the interfaces as /dev/vmnetN

---

### Post by illuniel on 2007-07-21
I see. 

PFsense is a firewall, router, load balancer, etc etc  with it, you need at least 2 NIC ports, one for the WAN, one for the LAN. 

I tried creating a PFsense installation on vmware and the ports it gave me were virtual ports. in other words, i had to use only 1 NIC or the LAN and access to the rest of the network was not possible.

how can i access the physical ports eth0 and eth1 for this machine or if that is possible so that i can assign a port for wan and lan using vmware :-)

---

### Post by illuniel on 2007-07-22
in a way, i kinda figured this one out.. 

[http://www.vmware.com/vmtn/appliances/index.html](http://www.vmware.com/vmtn/appliances/index.html)

there is a prebuilt VM appliance for these!! :KS:KS

gad's vmware is sure dang powerful. 

Thanks for your help and Guidance jtc!

---

