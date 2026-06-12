---
title: "Network bridging with changing interfaces"
date: 2010-09-15
forum: Virtualisation
---

### Post by kandresen on 2010-09-15
I am using a notebook with a virtual machine which I intend to use for development of web services, however, I am not permanently connected to any particular interface. At home I use wlan0 but no eth0, at work I use eth0 and no wlan0, yet again on the road I use mobile Internet through an usb dongle with yet another interface (mobnet0). 

If possible I would like the virtual machine to be accessible from the host without any network connected, just through a loopback interface to lets say 127.1.0.11 or so. 

What is the best way to set this up, and also leave it open for the virtual machine to do updates while on eth0 or wlan0 but NOT while I am using mobile Internet?

---

### Post by dmizer on 2010-09-16
This is easily done. All you have to do is change the networking settings in the virtual environment. If you have trouble doing this, please post what software you're using for your virtual host.

Edit:
Moved this to the virtualization section.

---

### Post by kandresen on 2010-09-16
I am trying to use virtualization using KVM with virt-manager. The problem is I am not connected permanently to any particular interface but need to be able to access the webserver etc. located inside the virtual machine through the regular web browsers on the host system. 

The network is currently configured with the default NAT network option which only allows the client system to connect to the Internet and not me to connect to it through the browsers on the host, and all the instructions I find require that I have eth0 for bridging. I have tried using recommendations meant for eth0 with lo (loopback) instead but this fails completely:

iface br0 inet static
	address 127.1.0.2
	network 127.1.0.0
	netmask 255.0.0.0
	broadcast 127.1.0.255
	gateway 127.1.0.1
	bridge_ports lo # replaced eth0 with lo and changed ip addresses
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off

So what can I do to make the web-server within the client system accessible from the host or other clients?

---

### Post by VcDeveloper on 2010-09-18
I have a VT built server and having same trouble bridging Qmenu-Kvm network, can't create a bridge with Virtual Manager 0.8.2 and trying to manually create the bridge in /etc/interfaces file.

kvm-ok
```

INFO: Your CPU supports KVM extensions
INFO: /dev/kvm exists
KVM acceleration can be used

```installed bridge-utils

Host (Static IP) ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:94:16:fd  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe94:16fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:215498 (215.4 KB)  TX bytes:53732 (53.7 KB)
          Memory:d2300000-d2320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4410 (4.4 KB)  TX bytes:4410 (4.4 KB)

virbr0    Link encap:Ethernet  HWaddr ce:f4:45:3f:c6:20  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::ccf4:45ff:fe3f:c620/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11165 (11.1 KB)

```My VM Webserver (Static IP) ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:94:16:fd  
          inet addr:192.168.122.11  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe94:16fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:215498 (215.4 KB)  TX bytes:53732 (53.7 KB)
          Memory:d2300000-d2320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```This is a virtual network example from [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging]("http://ubuntuforums.org/This%20is%20a%20virtual%20network%20example%20from%20https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging"):
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```Anything else I need to post and how do I create the bridge?

---

### Post by VcDeveloper on 2010-09-18
More Posts:

```
virsh net-list --all
Name                 State      Autostart
-----------------------------------------
default              active     yes     
```
```

brctl show
bridge name    bridge id        STP enabled    interfaces
virbr0        8000.d69466d8aa70    yes        vnet0

```

---

### Post by VcDeveloper on 2010-09-20
After doing so much reading and searching all over the place, it ends up being so simple.  BUT, the documentation doesn't give you any clue how to do it!  I ended up just running into it.

What they should of just said, is to create another interface settings in the **interface** file in /etc/network and gave an example like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.1.65
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```...then explain these settings are to reflect the host IP settings, then when you either when you create a VM, all you have to do is select this as the NIC or if you already have a VM, you would have to edit the .xml file and make the change to this:

```
    <interface type='bridge'>
      <mac address='52:54:00:24:9e:d9'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>

```this .xml file located in the folder /var/lib/libirt/images

The ones who make these documentation and tutorials should be keep in mind you have beginners and you shouldn't assume everyone knows what your talking about!  AND, be specific and detailed oriented!

I'm using the Virtual Machine Manager to create and manage my VM's.  I think I will do a tutorial using this approach just to show everyone how to do a tutorial the professional way!

---

### Post by kandresen on 2010-09-22
Unfortunately that simple solution does not work when no eth0 is connected, which is exactly my problem from the very beginning. I am most of the time not connected to any eth0. In fact, I am actually frequently sharing my wlan0 connection on eth0, simply put I cannot use eth0 for this. 

I can not use wlan0 neither, for I am not connected with that interface all the time neither, so I need it connect somehow on loopback (lo) in such a way I can connect to it from the host system and/or other virtual machines running locally on the same server. 

I have figured however I might have done this wrong initially and am now trying to configure it through "virtual machine manager" itself. Going to Edit -> Host Details and selecting the tab "Virtual Networks" and adding new network there. 

I call it something such as vlan10, then choose network range for example 127.200.1.0 then I have tried without dhcp, for "forward to physical network" selecting "Physical device lo" and mode "Routed", and save the changes. 

From there I Open my client virtual machine, "In details" I do "Add hardware" and select "Network". And add my newly created network card.

I then tried to configure the virtual client using fixed ip address on 127.200.1.1 with netmask 255.0.0.0 and route at 127.200.1.0 and restart the client. The network is claimed to be started correctly, however I can still not connect to it from the host system. 

How do I setup a virtual server in such a way that the client machines network services can be accessed from the host system over loopback interface, or in such a situation as when constantly moving between many alternative network interfaces such as eth0, wlan0, and mobilebroadband cards?

---

### Post by kandresen on 2010-09-24
I have found a temporary alternative solution until I come across a host based solution. What I did was installing OpenVPN on host and server, the current solution is as follows:

#host.conf
dev tun
ifconfig 10.8.0.1 10.8.0.2

#### END ####

#client.conf
remote 192.168.122.1 #IP of default virtual network card (vrbr0) created by the virtual server manager. 
dev tun
ifconfig 10.8.0.2 10.8.0.1

#### END ####

This allowed me to connect to the web server within the virtual client machine using [http://10.8.0.2](http://10.8.0.2) which so could be named in the /etc/hosts file. It is clearly not as good as setting this up on the host side, I do have some more ideas of how I might do this, but at least, I did manage to setup a solution that did not require additional encryption overhead and do mostly what I want with the exception of requiring installing openvpn on client and the host. SSH seems to work, but it also seem to freeze if inactive for a while(?). It can also seem like there is a time lag when connecting, but I have not yet tried too much. 

Despite working, I thus don't see this as resolved.

---

### Post by kandresen on 2010-09-24
My issue has been resolved!

I am realizing the problem was with the restrictive client system, not the host... What I finally did was running "tcpdump -i eth0" on the client machine, then I finally noticed that the connections went through but where blocked by firewall rules... :oops: 

I realized it as the openvpn connection worked when using ssh, but not when using web services... When realizing the real problem, I went back and tried again without the openvpn connection, and sure enough - the connection to the web server works from the client machine...

---

### Post by VcDeveloper on 2010-11-03
> **kandresen said:**
> My issue has been resolved!

I am realizing the problem was with the restrictive client system, not the host... What I finally did was running "tcpdump -i eth0" on the client machine, then I finally noticed that the connections went through but where blocked by firewall rules... :oops: 

I realized it as the openvpn connection worked when using ssh, but not when using web services... When realizing the real problem, I went back and tried again without the openvpn connection, and sure enough - the connection to the web server works from the client machine...

:) Congrat's!

---

