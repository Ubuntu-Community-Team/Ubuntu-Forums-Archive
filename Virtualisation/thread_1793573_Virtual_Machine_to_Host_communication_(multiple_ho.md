---
title: "Virtual Machine to Host communication (multiple hosts)"
date: 2011-06-29
forum: Virtualisation
---

### Post by YouBuntToo? on 2011-06-29
Hi!

My setup involves two hosts each running a few virtual machines. I'm using kvm/lib-virt(virt-manager) to run the VMs. The hosts are running ubuntu 11.04. The hosts are both going to the same router, gateway, etc.

I want the VMs on host1 to be able to 'see' host2 and be able to see the VMs running on host2 (I want to be able to ping them, transfer files between them, etc) . Does this involve bridged networking?

I've already tried setting up a bridged connection, but I can't get the VMs to connect to the internet or to see the other parts of the network. Just want to know if I'm on the right track.

Thanks

---

### Post by collisionystm on 2011-06-29
> **YouBuntToo? said:**
> Hi!

My setup involves two hosts each running a few virtual machines. I'm using kvm/lib-virt(virt-manager) to run the VMs. The hosts are running ubuntu 11.04. The hosts are both going to the same router, gateway, etc.

I want the VMs on host1 to be able to 'see' host2 and be able to see the VMs running on host2 (I want to be able to ping them, transfer files between them, etc) . Does this involve bridged networking?

I've already tried setting up a bridged connection, but I can't get the VMs to connect to the internet or to see the other parts of the network. Just want to know if I'm on the right track.

Thanks


If you are in bridged mode, your guest should be getting a local IP address from your router (or dhcp provider) is this happening??

And yes, to connect your VM's together on 2 different hosts, this generally requires bridged because you are using 2 separate elements that need to meet at a single access point. Hence the word bridge.

If you can't get a local ip address on your guest OS, this is a good indicator you do not have your bridging setup correctly. May I suggest using Virtualbox to run your guests and making your life 10x easier??

---

### Post by YouBuntToo? on 2011-06-30
Thanks for the reply.

I must not be setting up my bridge correctly because I don't get an IP on my VM. My /etc/network/interfaces file looks like this:

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
address 192.168.0.10
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0

I also added the IP of my host into the resolv.conf file. I really don't know what I'm doing wrong. The bridge shows up, and looks correct, if I do brctl show. Do you think I'm not getting a guest IP because I have a static setup in my interfaces file? My host has to have a specific IP address, but I would like the VMs to use DHCP. Any tips? Maybe an eth0 and an eth1?

I tried virtualbox today and I couldn't even get the VMs I am using to boot. It would finish installing and then try to boot but end up with some weird command line. I'm not sure what was going on. Anyway, I might work with that some more since it does seem like that would be easier.

Thanks again.

---

### Post by drdos2006 on 2011-06-30
Here is the contents of my Virtualbox server file /etc/network/interfaces.

iface eth0 inet static
	address 192.168.0.111
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1

Works fine but sharing is done through Virtualbox so I can access backup files.

regards

---

### Post by YouBuntToo? on 2011-07-01
Thanks for the response. I get the impression virtualbox really takes care of the details for you. Since I can't get that to work though, I'll have to make virt-manager work for now.
 
I need my hosts to have specific static IP addresses. I want to create a bridge to my guests. The guests need to have a DHCP assigned address within a very specific range. **How in the world do I do this?**
 
I understand how to make a bridge, but it is very important that the host have its correct static IP and the guest have a dhcp assigned IP. Using the /etc/network/interfaces file in my last post above I am getting a bridge but the guest never gets an IP. Maybe this should be expected since DHCP isn't mentioned anywhere in my config. 
 
Thanks for any help you guys can give me.

---

### Post by drdos2006 on 2011-07-01
Then you need to set up your Virtual Server as a DHCP server.
Try this.

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

regards

---

