---
title: "Create a virtual ubuntu server that is visible on the network by host and others"
date: 2009-10-07
forum: Server Platforms
---

### Post by dalefrancis88 on 2009-10-07
Guys,

Running into a problem, i am a microsoft developer and i only know enough linux to get by and do some basic administration.

What i am trying to do is create a VPC using Microsoft Virtual PC 2007 and the latest Ubuntu server, that i can use to start learning more about linux and wave. I have got the server installed and running and i have installed and configured openssh. i tried to configure the network interface and changed it to...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

i then opened and modified /etc/hosts to be...

127.0.0.1       localhost
192.168.0.100   waveserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

But i cant seem to be able to ping it from my host machine, or ping my host machine from the vm. i have disabled windows firewall and i have tried setting the network adapter to Shared and my network card. i also ran */etc/init.d/networking restart *after each file update.

Im kinda at the limit of my knowledge now guys, i really would appreciate any input you could give me. If possible i would like to stick with Microsoft Virtual PC because i know it and there is a high chance that it will go from my machine to a server running Microsoft Virtual Server.
I am hoping it will be just a matter of installing maybe a loopback adapter or editing some files :) let me know any ideas you have

---

### Post by dalefrancis88 on 2009-10-07
i forgot to mention that i am following these directions...[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by bogdan.veringioiu on 2009-10-07
Hi.

I have no experience with Ms Virtual Pc (i use vmware), but i get the feeling that this issue comes from the networking config for your guest (from virtual pc).

What do you have  as output for :
ipconfig /all
?
What ip do you have for your windows host?
Bogdan

---

