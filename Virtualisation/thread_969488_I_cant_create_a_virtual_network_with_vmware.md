---
title: "I cant create a virtual network with vmware"
date: 2008-11-03
forum: Virtualisation
---

### Post by gkjau on 2008-11-03
Im trying to create a virtual network between Ubuntu 8.04 64bits and vmware running WinXp. I dont know where to start.
Does anyone can help me?
Thanks :)

---

### Post by dubfazer on 2008-11-11
I presume you are using vmware workstation. The way that you do it is slightly different if your host (i.e. the os that runs workstation) is linux or windows, but the effect is the same. Workstation virtual machines have 4 types of network 
a) NAT - allows you to share the hosts IP address (basically you can run a virtual DHCP server or assign addresses that give your vm an IP to communicate with the host, but to any other machines on the physical network the traffic appears to come from the host IP. Thus if you set all your VMs to NAT they can communicate with each other, and with the outside world, but they share the same IP as the host for external physical communication. A good choice if you don't control the IP's available on your host. 
b) Bridged - allows your virtual machine to get an IP directly from the network, so your VMs appear as seperate machines on your physical network, with seperate addresses. If you use this approach then all vms and physical hosts can see each other on the same network.
c) Host Only - a private network only on your machine (so allowing your host and VMs to see each other, but not any other host on the physical network). Again you can run a virtual DHCP server for this host only network.
d) Custom - allows you to map virtual networks, to any other physical devices or configure networks as you like.
You configure the networks for a virtual machine by editing its settings. This is the same whether your OS is windows or linux.
On a windows host there is a menu item under edit that allows you to set up the virtual networks (i.e. map bridged or custom virtual to physcial, start / stop DHCP, set IP address ranges etc). On Linux you configure this when you install vmware, or by rerunning the vmware-config.pl. Hope this gets you started !

---

### Post by veloce on 2008-11-11
Only thing to add is that the most efficient network for communicating between host and vm is the host only network.

Also, I have had particularly poor results in using a bridged network to communicate between host and vm - this may have been fixed in later versions of vmware.

---

### Post by gkjau on 2008-11-13
I selected Host-only option but on ubuntu, i cant ping WinXP.
Is there a how-to?
Thanks

---

### Post by veloce on 2008-11-13
> **gkjau said:**
> I selected Host-only option but on ubuntu, i cant ping WinXP.
Is there a how-to?
Thanks

Don't know of a howto but you could search for one.  If you've got host only set up then you're most of the way there.

So the XP vm is getting an ip address? Can you ping the Ubuntu host?

Does either machine have a firewall running? (XP's will be running automatically and often gets in the way.)

---

### Post by gkjau on 2008-11-18
When i type ifconfig on Ubuntu(host) i see:
(beyond eth0 and lo)
> vmnet0
    Link encap:Ethernet  HWaddr 00:50:56:c0:00:00  
          inet addr:192.168.222.11  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1
    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.222.21  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8
    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.164.1  Bcast:192.168.164.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


and when i type ipconfig on WinXp i see:
> Adaptador Ethernet Conexão local:

        Sufixo DNS específico de conexão  . : 
        Endereço IP . . . . . . . . . . . . : 192.168.222.11
        Máscara de sub-rede . . . . . . . . : 255.255.255.0
        Gateway padrão. . . . . . . . . . . : 

Adaptador Ethernet Conexão local 2:

        Sufixo DNS específico de conexão  . : 
        Endereço IP de config. automática . : 169.254.54.84
        Máscara de sub-rede . . . . . . . . : 255.255.0.0
        Gateway padrão. . . . . . . . . . . : 


Since the IP are different i guess it isnt a network.
But if, on ubuntu, i ping vmnet1 and vmnet8 and i receive answers.
On WInXp, when i ping vmnet1's or vmnet8's IP i dont receive answers.

---

### Post by veloce on 2008-11-18
I assume your ubuntu host has it's eth0 address in the 192.168.54.X range?

Three issues I can see:

vmnet0 and vmnet1 are in the same address range.  I suspect that could cause some routing confusion.

Your xp has two interfaces (host only and bridged?) this may also cause confusion. 

Your eth0 network has a broadcast address of 255.255.0.0 so will interfere with all the vmnets.

I suggest:
Change your vmnets to be in the 10.0.0.X range
Remove the host only virtual adaptor from the xp vm.

---

