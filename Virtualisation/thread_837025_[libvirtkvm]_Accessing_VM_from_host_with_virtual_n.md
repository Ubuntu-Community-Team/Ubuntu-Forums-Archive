---
title: "[libvirt/kvm] Accessing VM from host with virtual networks"
date: 2008-06-22
forum: Virtualisation
---

### Post by gdwatson on 2008-06-22
I've gotten a Windows XP VM up and running with virt-manager and KVM on Hardy.  I want to access it from the host, so I have file sharing and remote desktop turned on, and Windows firewall off, but accessing 192.168.122.1 just doesn't do it.  It's the only VM running.

I edited /etc/sysctl.conf as [_suggested by the libvirt wiki_]("http://wiki.libvirt.org/page/Networking#NAT_forwarding_.28aka_.22virtual_networks.22.29").

I have the default network setup.  I want to avoid a manual bridge, if at all possible-- is that the only way to do this?

On the host:

```
gdwatson@gdwatson-laptop:~$ nmap 192.168.122.0/24

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-22 00:46 PDT
Interesting ports on 192.168.122.1:
Not shown: 1713 closed ports
PORT   STATE SERVICE
53/tcp open  domain

Nmap done: 256 IP addresses (1 host up) scanned in 2.629 seconds
gdwatson@gdwatson-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:fe:5c:3a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15867467 (15.1 MB)  TX bytes:15867467 (15.1 MB)

vnet0     Link encap:Ethernet  HWaddr f2:3b:06:f3:04:71  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::f03b:6ff:fef3:471/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:135510 (132.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:91:0c:55  
          inet addr:192.168.55.103  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe91:c55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4220749 (4.0 MB)  TX bytes:806883 (787.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-91-0C-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

gdwatson@gdwatson-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.55.0    *               255.255.255.0   U     0      0        0 wlan0
192.168.122.0   *               255.255.255.0   U     0      0        0 vnet0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.55.1    0.0.0.0         UG    0      0        0 wlan0
gdwatson@gdwatson-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
gdwatson@gdwatson-laptop:~$ 
```

And now that I've posted all that it'll be something obvious.  ;)

---

### Post by gdwatson on 2008-06-24
This can't be a terribly unusual thing to do-- someone must know the answer, right?

---

### Post by seetho on 2008-06-24
I've done a lot of digging around while setting up my server recently and I think bridge is the only way to go.

You can create a network bridge to the NIC on your host as described in:
```
https://help.ubuntu.com/community/KVM
```

On me system I had two NICs and I bridge one of the to the internal network of the VMs.  This way I have access to all VMs running on the host.  I think you should be able to do the same with only one NIC.  However you should be careful if your host is exposed to the internet.

Here's my /etc/network/interfaces on my server host:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
# Onboard Intel NIC
# Host connection to the internet
auto eth0
iface eth0 inet static
	address 192.168.1.98
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.2


# Secondary network interface
# Marvell PCI NIC
# For internal LAN only
auto eth1
iface eth1 inet manual
	
# Bridge network for guest OSes (to eth1)
auto br0
iface br0 inet static
	address 192.168.1.97
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	bridge_ports eth1
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off

```

It took me some time and a lot of digging around to get it right.  Try it and see how it goes.

Good luck.
seetho

---

### Post by seetho on 2008-06-24
Forgot something else... You have to edit your VMs to make use of this bridge now.

Edit the file /etc/libvirt/qemu/<vmname>.xml (where <vmname> is the name of your VM in your system).

```
    <interface type='bridge'>
      <mac address='00:16:3e:3c:7f:a1'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
```

Of course you should find out the MAC address of your bridge NIC.

Anytime you make changes to the XML file of the VMs you have to redefine them for the changes to take effect:

```
sudo virsh define /etc/libvirt/qemu/<vmname>.xml
```

It should work now.

You can also make the modifications in the template xml file so that any new VMs you create will use the bridge NIC as default.  This documented in the link I gave in my post above.

seetho

---

### Post by gdwatson on 2008-06-25
Thanks.  I'd read something about bridges and dynamic/wireless connections not getting along.  This is on my laptop-- do you know if this requires a static IP, or is that just how you have it setup?

---

### Post by seetho on 2008-06-26
Most of the docs i've found online says bridges and some wireless don't play well together.  I've not tried it so I can't confirm.  My server and all the VMs are on static IPs.

Another thing is I use dnsmasq on the host pc to resolve hostnames of all my VMs.  So if you can get your bridge to work with your wireless with dynamic IPs you can still access all your VMs by name.

---

### Post by carlodin on 2008-06-30
Heya guys Im interested in this aswell. Have a new Hardy box running here beside me smoothly. 

So the thing I ran into was how to set up a firewall so I could close all ports on my host *(except 22)* without killing the bridge.

How did you get your host system to not use the eth1 seetho?

Edit:
I only got 1 NIC but if its possible to do this if I have 2 then Il chop in another NIC.

---

### Post by seetho on 2008-06-30
> **carlodin said:**
> Heya guys Im interested in this aswell. Have a new Hardy box running here beside me smoothly. 

So the thing I ran into was how to set up a firewall so I could close all ports on my host *(except 22)* without killing the bridge.

How did you get your host system to not use the eth1 seetho?

Edit:
I only got 1 NIC but if its possible to do this if I have 2 then Il chop in another NIC.

Yup, got the basic infrastructure of my virtual system up and running (on 2 NICs).  All VM services are accessible on internal network and from outside via SSH thru the host server NIC.  Only port 22 on the server is open.  Everything else is closed to outside.  It's running behind a NAT router anyway so it's relatively safe.

More details when I get home from work...

seetho

---

### Post by carlodin on 2008-07-01
Do you got a firewall on your host seetho that restricts your host connecting through the bridge?

Don't think you need an Ip on the bridge.

Atm I think I will manage with it as it is. The only "open" service on my host are apache *(that got a little dokuwiki on it that is used as a storage for "good to know commands")* and that one I can set to only listen on localhost.

So my problem is solved or never where there...

---

### Post by seetho on 2008-07-01
> **carlodin said:**
> Do you got a firewall on your host seetho that restricts your host connecting through the bridge?

Don't think you need an Ip on the bridge.


I'm still in the process of setting up my server, so i'll not bother with firewalls at the moment.  My router NAT effectively acts as a firewall anyway.  The only way in through the router is SSH.  Even this I've configured to public key authentication only - no password logins.  Only trusted machine with valid private keys have access.

I have a 2 VMs running: Samba as file server; Apache2 as intranet server.  Later I will test more: Mail server; sftp server; etc.

All of them are accesible on the internal LAN.  They can be accessed from outside via SSH tunnel.

I gave my bridge an IP address.  Technically you don't have to assign it an IP address.

I create all my VMs with virt-install with the option "--network bridge:br0".  This will connect the virtual NIC of the VM to my bridge br0 which is actually eth1.  Thus all VM traffic go through this NIC.

seetho

---

### Post by carlodin on 2008-07-01
Thanks for the feedback seetho ;)

Back to gdwatsons problem.

I think aswell that bridge is the way to go.
Here is my interface file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# Bridge for virtual systems
auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

As I have no services going on my host I have no troubles with firewall etc. Only got ssh open.

seetho:
Im having troubles with my keyboard when connecting to VMs through VNC. Im sitting here right now and can't logg into one of my VMs as I can't type my password. The network is down on the VM so I can't connect directly with ssh.

---

### Post by Jamm3r on 2008-07-01
Hey guys sorry to but in the conversation but i have been playing around with kvm/libvirt and networking.  I was able to set it up using a bridged connection to connect to the VM's.  I noticed Seetho that you used dnsmasq, which is what i think i might need to figure out my problem.

What i am trying to do is set up all the VM's so they access the outside network with the hosts ip.  That is sort of like a router where the hosts ip is visible but all the other VM's are masked and can be accessed through ssh.  Any ideas or does anyone know if this is even possible?

And BTW i have a decent tutorial on how to set up vm with networking and using virsh if anyone wants it.

---

### Post by carlodin on 2008-07-01
Love tutorials ;)

---

### Post by gdwatson on 2008-07-09
So I've been poking around a bit more, and I noticed that the Windows VM thinks it's on the 10.0.2.0/24 subnet, and it's 10.0.2.15, which I remember from previous versions and pre-libvirt days.

Is the libvirt NAT setting supposed to do that, or is the VM supposed to know it's on 192.168.122.0/24?  It seems to connect to the outside world just fine, but I haven't found anything else about connecting to the VM without a bridge.

**Edit:**  So that caused me to start poking around, and it looks like I have user-mode networking on the VM, despite having followed a guide and been in the proper groups.  How do I get virt-manager to switch it to the standard NAT-type networking?

---

### Post by gdwatson on 2008-07-10
It seems the most important thing I had missed was the importance of running virt-manager as root.  I did edit the XML file to change the network type according to [http://libvirt.org/formatdomain.html](http://libvirt.org/formatdomain.html), but the big thing was missing that little detail.  :-P

---

