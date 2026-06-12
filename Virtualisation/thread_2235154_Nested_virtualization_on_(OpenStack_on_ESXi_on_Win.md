---
title: "Nested virtualization on (OpenStack on ESXi on Windows)"
date: 2014-07-19
forum: Virtualisation
---

### Post by robert-pavlovic1 on 2014-07-19
[TABLE]
[TR]
[TD="class: postcell"]For the last few weeks I have been reading a lot about OpenStack, Cloud Computing, virtualization, VMware tools and I have decided to try it. I would like to install, configure it and try it to see how it works. For the last few days I have had troubles installing it.
I want to try it install on my laptop in an appropriate way as in a server room. Now I am a little bit confused, and I would like to get some help with the network configuration and get answers for my questions. Can one one explan mi how to do it.

My laptop specifications:
     
CPU: Core i5, dual core 2.5Ghz with Intel virtualization technology
     RAM: 6GB
     SSD: 256GB
     One LAN adapter
     One WLAN adapter (I am not using this at all)
     OS: Windows Windows 7 64-bit

I am using VMware Workstation 9, ESXi 5.5 and vSphere, I don't use vCenter or vSphere web application.
Inside a VMware Workstation I have installed ESXi 5.5 with specification:
     
RAM 2GB, 
     2 processors, 
     1 network adapter using NAT
     hostname: localhost
     IP Address: 192.168.186.140
     Network identit acquired from DHCP server 192.168.186.254

Inside ESXi I have the option "Test Management Network" where I can ping some IPs, It works.
     
Ping Address #0: 192.168.186.2
     Ping Address #1: 192.168.186.2
     Ping Address #2: blank
 Resolve Hostname localhost.localdomain

I haven't made any configuration inside ESXi and for ESXi in workstation I am using NAT and enabled option "Synchronize guest time with host". With vSphere I connect to ESXi by using IP: 192.168.186.140, username and password.
Inside vSphere I have two virtual machines installing Ubuntu server 14.04, and my plan later is to install OpenStack on it.
Specifications of both virtual machines is the same (I will change it later if there will be any need):
     
CPU 1
     RAM 512 MB
     One network adapter using VM Network

The first virtual machine is a CONTROLLER node and second virtual machine is COMPUTE. CONTROLLER I want to use as controller node for OpenStack, other as a compute node. I have started with installation of OpenStack components by following the instructions from the install guide. That means I will use two nodes installation. I have come to this step:[http://docs.openstack.org/icehouse/install-guide/install/apt/content/basics-networking-nova-verify.html](http://docs.openstack.org/icehouse/install-guide/install/apt/content/basics-networking-nova-verify.html)and I have problem with pinging from CONTROLLER to COMPUTE and inversely. I can ping google.com.
I thought I will resolve this issue later and move on with the installation. In point four of this section:[http://docs.openstack.org/icehouse/install-guide/install/apt/content/keystone-install.html](http://docs.openstack.org/icehouse/install-guide/install/apt/content/keystone-install.html) when I type:
 
     su -s /bin/sh -c "keystone-manage db_sync" keystone 

get this error:
     
2014-07-18 19:30:30.682 6656 CRITICAL keystone [-] OperationError: (OperationalError)  (2005,   
     "Unknown MySQL server host 'controller' (0)") None None

I have been googled it and found out that there is something wrong with my network configuration, which means there is something wrong with localhost which takes us back to the network problem.
Netowork interfaces and host of bouth Ubuntu servers:

CONTROLLER NODE:
cat /etc/network/interfaces
     
auto lo
     iface lo inet loopback
     auto eth0
     iface eth0 inet dhcp
     address: 10.0.0.11 //AS IN INSTALLATION GUIDE
     netmask 255.255.255.0
     gateway 10.0.0.1

cat etc/hosts
     
127.0.0.1 controller
     #controler 
     10.0.0.11 controller
     #compute
     10.0.0.31 compute

COMPUTE NODE:

cat /etc/network/interfaces

     auto lo
     iface lo inet loopback
     auto eth0
     iface eth0 inet dhcp
     address: 10.0.0.31 //AS IN INSTALLATION GUIDE
     netmask 255.255.255.0
     network 10.0.0.0
     gateway 10.0.0.1
     auto eth1
     iface eth1 inet manual
     up ip link set dev $IFACE up
     down ip link set dev $IFACE down

cat etc/hosts
     
127.0.0.1 compute
     #compute 
     10.0.0.31 compute
     #controler 
     10.0.0.31 controler

Before I begin work with installing OpenStack components and before that, solving this issue I have some questions:
Is it possible on laptop to install in this way OpenStack? I know it is much easier using devstack one node installation (I have already tried it) but I would like to now how OpenStack works, what exactly is virtualization, how to launch virtual machine inside OpenStack. Don't get confused with virtual machines inside VMware and vSphere.
Is it possible to have nested virtualization, so that the first virtualization is on workstation and ESXi for Ubuntu server virtual machine, and the second virtualization is inside OpenStack for providing instances with flavor settings?
Can anyone help me with configuring these network problems, obviously I cannot continue with OpenStack installation. Should I use virtual switches and routing? I would like to have management network and public network so I can't inside Windows browser get horizon and launch some instances. I install LAMP on it. Because I just want to get proof of this concept.
Should I configure network on both Ubuntu servers and also inside vSphere? I think I should.
I do not understand IPs on ESXi "Test Management Network" used for ping tests. Because IP of ESXi is 192.168.186.140.[/TD]
[/TR]
[/TABLE]

I want to achieve something like this guy did: youtube.com/watch?v=I2gBypQaxqk. Below is a picture of my network in vSphere: [http://postimg.org/image/3kua5hx2l/](http://postimg.org/image/3kua5hx2l/)

I would like to do on VMware tools as this guy do it VirtualBox. [http://uksysadmin.wordpress.com/2011/02/17/running-openstack-under-virtualbox-a-complete-guide/](http://uksysadmin.wordpress.com/2011/02/17/running-openstack-under-virtualbox-a-complete-guide/) [http://uksysadmin.wordpress.com/2011/02/24/running-openstack-under-virtualbox-a-complete-guide-part-2/](http://uksysadmin.wordpress.com/2011/02/24/running-openstack-under-virtualbox-a-complete-guide-part-2/)

---

### Post by TheFu on 2014-07-19
Welcome to the forums.

WOW!  That is a long 1st post here.  TL;DR.  I'll comment on keywords that I've seen, however. It probably isn't useful, but ... 

network 10.0.0.0 <---- doesn't seem correct to me from the interfaces file.

I love VMs and have used most of the VM technologies available (except from MS) over the years.  Since this is an all-volunteer forum, you may find that more complex questions don't get answered or aren't answered to the level you'd like.  I've given VM optimization presentations around the world (ok, just in 5 countries, 3 continents).

As to networking - the basis for Linux bridging is er ... the linux bridge. It is part of bridge-utils and it works.  Linux-based routers and switches work with this and seem to handle it just fine.  If you need very high-end bridging, then openvswitch is probably what you want, but only if you have 10G or faster connections (IMHO). For GigE the normal linux bridges work great.  I don't trust any GUI tool to create or manage these.  For a few years, the automatically generated bridges for LXC and QEMU and KVM haven't been as stable as the base Linux bridges manually made (which haven't given my any issues at all.  Has that changed? I dunno - configuring a linux bridge on my KVM hosts is automatic now (thanks to ansible rules).

ESXi - it requires a Windows desktop to manage it. No thanks.  KVM is stable, just as fast (if not faster), and supports many more HW configurations than the approved hardware that works on ESXi.  Out of 6 systems here, only 1 could load ESXi due to the HW compatibility limitations.  OTOH, any company running ESXi with a legal license probably can pay the admin a little better too. Don't get me started on the cost of upgrades to do anything. 

Can you have nested virtualization? Well - er .... yes, but you shouldn't, at least not for HVM setups.  It is unclear how much virtualization you've done already (besides reading) - if you have 2 yrs experience, perhaps trying nested virtualization for fun is useful. Otherwise, I fear the confusion of thinking "inside a VM". A good understanding of networking will be needed too - beyond a typical home user's knowledge. If you insist on doing this, the hostOS will need to pass thru to every clientOS the hw-extensions for VT-x. I've see that setting inside virtualbox, but never tried it myself.  Haven't looked in my production KVM systems, so I can't say how easy that is.

For containers, knock yourself out. Run a container under an HVM (or not) or nested below a container, below a container, below a container ... please post the results (worked/didn't) and any performance data you capture. With KVM, openvz, qemu, Docker, lxc and other non-commercial VM technologies, the license agreement doesn't prevent posting benchmark data ... er ... like those proprietary offerings.

Openstack. Ask anyone doing openstack, the best way to learn about OpS is to run the opendev release on dedicated hardware.  It is fairly complex and there are hundreds of moving parts. Based on previous questions here about it, I suspect you'll get better answers at the openstack forums. I don't use it, but if I was planning to be cloud or enterprise-cloud architect, I'd definitely learn it.  The days are numbered for VMware in the Linux enterprise, IMHO.

In summary,
* Should you load VMs inside VMs?  No.

* Should you load container-based app-instances inside VMs?  Sure.

* Should you load openstack and any other HVM solution on the same hardware? Nope.

* Should you load ESXi and any other HVM solution on the same hardware? Nope.

* Where does virtualbox, VMware Player, workstation sit in this discussion? They are desktop VM tools, not to be confused with server VM tools.

* I hear about type-1 and type-2 hypervisors, what's up with those? Which is "better", for all values of better?  I consider this all marketing crap. On a server with 96G of RAM, does a VM host OS that uses 200M or 1G matter when the 1G buys huge amounts of flexibility and doesn't force a client into buying commercial software for anything not included in the base offering?

Sorry to rant - hope a tiny bit helped.

---

