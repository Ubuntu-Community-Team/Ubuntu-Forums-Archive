---
title: "Home Server Setup - Partition &amp; Software Help"
date: 2008-07-21
forum: Server Platforms
---

### Post by browneye253 on 2008-07-21
I've recently pieced together some hardware I've had lying around the house for sometime and decided to construct a home server to fill a couple of roles but I need a little bit of guidance.

My first question is in regards to partitioning.  I have 3 harddrives that I'm going to install in the system (2) 40gb and (1) 120gb.  My goal is to have as much storage space as possible and at the moment I'm not concerned with any sort of RAID configuration.  What is the best way for me to partition and format these drives to accomplish my goal? I will be accessing this share with Windows PC's as well.

My second question is in regards to software and the role in which I want the server to function.  I currently have a box setup and running pFsense and have had it working fine for over a year now.  Is it possible to combine the new server and the old pFsense box into the same machine?

I'm sure I'll have more questions as I progress but answers to these should get me headed in the right direction.

---

### Post by bodhi.zazen on 2008-07-21
Not sure what you are asking about storage space. partitioning does not change the available HD space.

Similar problem in terms of a server ? What kind of server ? you could install server software on pfsense ? Otherwise you would need to set up similar servers on the new install (almost any distro can act as a firewall /router, the configuration may be a little different).

I would advise against using the same box as both a router / firewall and server, unless you are behind a router.

One option for you may be openvz (you could install the openvz kernel and keep the server separate from the router / firewall). Openvz has a smaller footprint then VMWare/ Virtualbox/KVM.

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

---

### Post by browneye253 on 2008-07-21
In regards to the storage space, I understand the partitioning doesn't effect total HD space, I was just curious what partitioning scheme would be best to use for the drive?  I only need a swap partition on the main drive correct?  And should I use ext3 for the other drives or NTFS?

With OpenVZ, I would be able to run two virtual machines with one using pFsense and the other Ubuntu Server.  With this setup would I need to have 3 Nic cards in the machine or can I still accomplish everything with 2 Nic cards?

---

### Post by windependence on 2008-07-21
I would run VMware server on the box and then run pfsense in a VM. FreeBSD runs great in a VM and that's what pfsense runs on (good choice BTW). 

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

Then, you can run whatever other VMs you want on the box and just treat your pfsense VM as your gateway. The other VMs will think it's a real box and since the connections are virtual between them, VMware doesn't route it out and then back in again, the traffic will go right to the pfsense Vm on the same box without traveling through switches and cable and it will fly!

I am thinking about doing this myself. BTW how is pfsense working for you? Configuration was easy? Just curious.

-Tim

---

### Post by bodhi.zazen on 2008-07-21
> **windependence said:**
> I would run VMware server on the box and then run pfsense in a VM. FreeBSD runs great in a VM and that's what pfsense runs on (good choice BTW). 

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

Then, you can run whatever other VMs you want on the box and just treat your pfsense VM as your gateway. The other VMs will think it's a real box and since the connections are virtual between them, VMware doesn't route it out and then back in again, the traffic will go right to the pfsense Vm on the same box without traveling through switches and cable and it will fly!

I am thinking about doing this myself. BTW how is pfsense working for you? Configuration was easy? Just curious.

-Tim

Have you looked at OpenVZ ? Less overhead then VMWare and perfect for the kind of tasks you are describing. The OpenVZ project also contributes to the Linux kernel and the openvz kernel is in the Ubuntu repos.

---

### Post by windependence on 2008-07-21
Can you run *BSD guests on OpenVZ?

-Tim

---

### Post by browneye253 on 2008-07-21
> **windependence said:**
> I would run VMware server on the box and then run pfsense in a VM. FreeBSD runs great in a VM and that's what pfsense runs on (good choice BTW). 

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

Then, you can run whatever other VMs you want on the box and just treat your pfsense VM as your gateway. The other VMs will think it's a real box and since the connections are virtual between them, VMware doesn't route it out and then back in again, the traffic will go right to the pfsense Vm on the same box without traveling through switches and cable and it will fly!

I am thinking about doing this myself. BTW how is pfsense working for you? Configuration was easy? Just curious.

-Tim

pfsense has worked great so far.  The setup was quick and painless and configuring it was a breeze.  I only switched to it because my other router died and I didn't want to spend the money on a new one.

---

### Post by browneye253 on 2008-07-22
Ok, I spent last night reading and reading some more about the various options of Virtualization software. 

[http://ubuntuforums.org/showthread.php?t=617225](http://ubuntuforums.org/showthread.php?t=617225)

In the above post you mention that OpenVZ can't run FreeBSD which is what pFsense runs on so I think that one is not going to be an option.

I realize that VMware might not be the lightest option for me but at the moment it seems to have the most support which I think I will need since this is my first go at virtualization.

I want to clarify what I think I have learned.  In order to install VMware I need a host OS installed.  I'm planning to go with Ubuntu for this but I believe it needs to be ubuntu desktop or at least Ubuntu Server with a GUI.  I can't seem to find any tutorials that show CLI instructions only GUI.  

My current goals are still the same to have pFsense and a flavor of linux running to do my file sharing, dns, webserver.  

Thanks for the help.

---

### Post by windependence on 2008-07-22
No GUI necessary, and you should run server because the kernel is optimized several ways for virtualization.

Here is a great tutorial all from the command line:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Also:

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

-Tim

---

### Post by bodhi.zazen on 2008-07-22
My mistake re : OpenVZ and BSD

I looked through the links and it appears OpenVZ is being ported to FreeBSD (don't know why on that one, lol) but as of now will not run in OpenVZ (you would need to configure BSD to run on a linux kernel).

You can run VMWare server (and workstartion) without a gui :

[http://www.vmware.com/support/ws5/doc/ws_learning_cli_vmrun.html](http://www.vmware.com/support/ws5/doc/ws_learning_cli_vmrun.html)

---

