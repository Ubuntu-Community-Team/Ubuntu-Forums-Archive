---
title: "Ubuntu Server Network Configuration"
date: 2011-11-03
forum: Server Platforms
---

### Post by psoheil on 2011-11-03
Hello All,

Although I have been working with linux server for years, this is the first time I am attempting to install and configure networking on one from scratch. What I am trying to do is:

1. Install Ubuntu Server on a Virtual Box Machine. (Done).
2. Configure this new Ubuntu Server to Serve Web Pages on the local network and allow SSH Connections. 

Step 2 is where I am having problems. I have a local Workgroup Linksys Router that looks like this:

_Local Area Connection:_

Default Gateway: 192.168.1.1
DHCP Server: 192.168.1.1
Subnet Mask: 255.255.255.0

_Virtual Box Connection:_

IPv4 Address: 192.168.56.1
Subnet Mask: 255.255.255.0

Initially after Ubuntu Server Installation, it was configured for DHCP:

IP Address for eth0: 10.0.2.15

But I wasn't able to either connect to the Server using HTTP or SSH, so I modified network interfaces as follows:

```
$> sudo vi /etc/network/interfaces
```I changed the content of the file from this:

```

auto eth0
iface eth0 inet dhcp

```To this:

```

auto eth0
iface eth0 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```I then edited the DNS settings:

```
$> sudo vi /etc/resolv.conf
```And added the DNS Server IP of my ISP for name server and removed the DHCP Client:

```
$> sudo apt-get remove dhcp-client
```Last but not least, I restarted the networking component:

```
$> sudo /etc/init.d/networking restart
```Hoping that this did the trick, I tried pinging google.com with no luck. I am also still not able to access either SSH or HTTP (using [http://192.168.1.120](http://192.168.1.120)) from any other computer on the same network. Anyone have any suggestions or idea why it's not working?

Thanks!
Pete

---

### Post by volkswagner on 2011-11-04
I am not all that familiar with VB, but I believe your trouble lies with the network settings in VirtualBox for your guest.

Take a look here under "Host Networking", you may need to setup bridged network connection.

[https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)

---

### Post by haqking on 2011-11-04
192.168.56.1 is a different network (subnet) than the router and host

I trust it is using bridged networking and not NAT which is default

---

### Post by psoheil on 2011-11-04
> **volkswagner said:**
> I am not all that familiar with VB, but I believe your trouble lies with the network settings in VirtualBox for your guest.

Take a look here under "Host Networking", you may need to setup bridged network connection.

[https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)

Thank you for the link. I followed the Bridge setup steps but got stuck on this step:

> **Declare virtual interfaces which will be used by VirtualBox**



The directory /etc/vbox/interfaces does not exist on the virtual server, and my VM Host is actually a Windows 7 machine, so the directory in question does not exist there either. :(

> **haqking said:**
> 192.168.56.1 is a different network (subnet) than the router and host

I trust it is using bridged networking and not NAT which is default

By default the Network setting of the Virtual machine was set to NAT. 

Thanks,
Pete

---

### Post by haqking on 2011-11-04
choose the network interface you want to bridge too in the VM settings. such as WLAN or ETH whatever one is connected to your network on your host.

Choose bridged mode for that interface.

Fire up your VM and assign a static valid for your network

Thats it.

Or have you done that and its not working ? i was confused by your  multiple IP addresses.

---

### Post by psoheil on 2011-11-04
> **haqking said:**
> choose the network interface you want to bridge too in the VM settings. such as WLAN or ETH whatever one is connected to your network on your host.

Choose bridged mode for that interface.

Fire up your VM and assign a static valid for your network

Thats it.

Or have you done that and its not working ? i was confused by your  multiple IP addresses.

I have already tried that with no luck. :(

---

### Post by drdos2006 on 2011-11-04
Your server needs to be on the same sub-net as your router to see the router. As haqking says, bridged mode and gateway is 192.168.1.1


regards

---

