---
title: "Networking Issue post Virtualbox and Samba install"
date: 2017-05-20
forum: Virtualisation
---

### Post by mocadedhed2 on 2017-05-20
[FONT=arial]Hi - I have a pretty clean install of 16.04 - only installed virtualbox since I set up the system. Earlier today I tried to get the Windows 10 machine to bridge to the Ubuntu 16.04 network adapter and I'm sure I've screwed something up. after installing Samba to try to get the Win 10 machine running in VB to be seen by the windows network that this Ubuntu system is connected to (physically).

I can't connect to the network now. It's like the eno1 connection is still stuck in some kind of mode that won't let it get an ip address.
I've tried stopping and starting the network service. as well as nano editing the /etc/network/interfaces file to:

auto eno1
iface eno1 inet dhcp

The system refuses to grab an ip address from the router.

ifconfig - a is returning lo info, eno1 info (no ip address assigned). as well as eno1:avahi (indicating a failed attempt to get an ip address).

desperate for any help. At this stage I'm not even dealing with the virtualbox connectivity. just native Ubuntu OS on the system itself.
Thank you in advance.
[/FONT]

---

### Post by SeijiSensei on 2017-05-21
Your post is a bit confusing so let me see if I understand your situation.  You have an Ubuntu host running VirtualBox with a Windows 10 guest?  And you want to configure the guest's connection to use "bridged networking."  Is that correct?

In my experience, all I've needed to do was switch the interface from "NAT" to "Bridged" in the VB network settings for the virtual machine.  After that, the VB guest would make a DHCP request out on the host's network and get an address in the same subnet.  There's no reason to be futzing with things like /etc/network/interfaces on the Ubuntu host.  If the host gets an address successfully via DHCP, the guest should as well.

---

### Post by wildmanne39 on 2017-05-21
*Thread moved to **Virtualisation**.*

---

