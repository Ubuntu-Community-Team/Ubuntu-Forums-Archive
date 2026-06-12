---
title: "Problems with network bridge settings on Ubuntu 14.04 LTS"
date: 2014-08-30
forum: Virtualisation
---

### Post by Merridion on 2014-08-30
I have a dedicated server (hosted with OVH / SyS in their Canada data center with 4 additional static IPs - "FailOverIps") that I'm setting up to run KVM on Ubuntu 14.04 LTS as a virtualization host server with a minimum of two (2) virtual machines (1 as a basic host, 1 as a test host) 
   
  I've originally set up virtualization on the host o/s with VirtualBox, but changed my mind and decided to go with KVM. Either way, I did NOT have the virtual machines configured to work over the network bridge - I never got to that point in VirtualBox.
   
  My problem is setting up the network bridge to work with KVM - I've looked over the Ubuntu guides (and several across the web) and I think I've over-adjusted the code required in the "/etc/network/interfaces" file. Instead of showing all the mistakes I've made, I'll post the basic bridge setup I have that works for the server:
   
   
  ```

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address xxx.xxx.xxx.xxx [COLOR=#FF0000] <--(changed to my dedicated server's IP address)[/COLOR]
        netmask 255.255.255.0
        broadcast xxx.xxx.xxx.255 [COLOR=#FF0000] <--(changed to my dedicated server's IP address + "255")[/COLOR]
        network xxx.xxx.xxx.0 [COLOR=#FF0000] <--(changed to my dedicated server's IP address +"0")[/COLOR]
        gateway xxx.xxx.xxx.254 [COLOR=#FF0000] <--(changed to my dedicated server's IP address + "254")[/COLOR]
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```   
   

  With the bridge setup above, I can ping the server and it works. It's when I start making adjustments to add in the additional static IPs for any additional virtual machines that I get totally lost.  I've read too many different guides and I think I may have "over-coded" the changes to the point that I made it not work. Here's one static format that I've seen:
   
   ```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address xxx.xxx.xxx.xxx [COLOR=#FF0000] <--(changed to my dedicated server's IP address)[/COLOR]
        netmask 255.255.255.0
        broadcast xxx.xxx.xxx.255 [COLOR=#FF0000] <--(changed to my dedicated server's IP address + "255")[/COLOR]
        network xxx.xxx.xxx.0 [COLOR=#FF0000] <--(changed to my dedicated server's IP address +"0")[/COLOR]
        gateway xxx.xxx.xxx.254 [COLOR=#FF0000] <--(changed to my dedicated server's IP address + "254")[/COLOR]
      
       post-up /sbin/ifconfig eth0:0 [COLOR=#FF0000](FailOverIP-1)[/COLOR] netmask 255.255.255.255 broadcast [COLOR=#FF0000](FailOverIP-1)[/COLOR]
       post-down /sbin/ifconfig eth0:0 down

       post-up /sbin/ifconfig eth0:1 [COLOR=#FF0000](FailOverIP-2)[/COLOR] netmask 255.255.255.255 broadcast [COLOR=#FF0000](FailOverIP-2)[/COLOR]
       post-down /sbin/ifconfig eth0:1 down

       post-up /sbin/ifconfig eth0:2 [COLOR=#FF0000](FailOverIP-3)[/COLOR] netmask 255.255.255.255 broadcast [COLOR=#FF0000](FailOverIP-3)[/COLOR]
       post-down /sbin/ifconfig eth0:2 down

       post-up /sbin/ifconfig eth0:3 [COLOR=#FF0000](FailOverIP-4)[/COLOR] netmask 255.255.255.255 broadcast [COLOR=#FF0000](FailOverIP-4)[/COLOR]
       post-down /sbin/ifconfig eth0:3 down

```
  

  And here's another static format:
   

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address xxx.xxx.xxx.xxx [COLOR=#FF0000] <--(changed to my dedicated server's IP address)[/COLOR]
        netmask 255.255.255.0
        broadcast xxx.xxx.xxx.255 [COLOR=#FF0000] <--(changed to my dedicated server's IP address + "255")[/COLOR]
        network xxx.xxx.xxx.0 [COLOR=#FF0000] <--(changed to my dedicated server's IP address +"0")[/COLOR]
        gateway xxx.xxx.xxx.254 [COLOR=#FF0000] <--(changed to my dedicated server's IP address + "254")[/COLOR]
      
auto eth0:0
iface eth0:0 inet static
       address [COLOR=#FF0000](FailOverIP-1)[/COLOR]
       netmask 255.255.255.255
       broadcast [COLOR=#FF0000](FailOverIP-1)[/COLOR]

auto eth0:1
iface eth0:1 inet static
       address [COLOR=#FF0000](FailOverIP-2)[/COLOR]
       netmask 255.255.255.255
       broadcast [COLOR=#FF0000](FailOverIP-2)[/COLOR]

auto eth0:2
iface eth0:2 inet static
       address [COLOR=#FF0000](FailOverIP-3)[/COLOR]
       netmask 255.255.255.255
       broadcast [COLOR=#FF0000](FailOverIP-3)[/COLOR]

auto eth0:3
iface eth0:3 inet static
       address [COLOR=#FF0000](FailOverIP-4)[/COLOR]
       netmask 255.255.255.255
       broadcast [COLOR=#FF0000](FailOverIP-4)[/COLOR]


```
   
  
  I'm unsure how to adjust any of the "static" samples to fit with the network bridge (br0) that currently works.  I've experimented a bit, but I cannot ping any of the "FailOverIPs". Any tips or suggestions would help a lot.

---

### Post by TheFu on 2014-08-31
The gateway needs to be the network gateway, not the hostOS.
Forget the failover examples. They are just confusing you.
The real card needs to be in the list, but not configured.

Inside the VM, normal eth0 config is needed - just like it was a physical server.
An example ... that works for many KVM VMs - hostOS:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
  address 172.22.22.6
  gateway 172.22.22.1
  netmask 255.255.255.0
  broadcast 172.22.22.255
  dns-nameservers 172.22.22.1
  dns-search example.com example.lan
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

---

### Post by Merridion on 2014-09-01
TheFu, thanks for the response!

So I shouldn't make any settings in the "interfaces" file of the Host o/s for any virtual machines? All those settings will be set WITHIN the "interfaces" file of the virtual machine (guest o/s)?

---

### Post by Doug S on 2014-09-01
> **Merridion said:**
> So I shouldn't make any settings in the "interfaces" file of the Host o/s for any virtual machines?No. > **Merridion said:**
> All those settings will be set WITHIN the "interfaces" file of the virtual machine (guest o/s)?Yes.

---

### Post by TheFu on 2014-09-02
Doug-S nailed it.  

The VM-host provides virtual devices.  The guestOS should recognize those devices and provide drivers to access them.  Just remember that the guestOS doesn't know about the real-hardware in the system unless you go way-way-way out of your way to allow a passthru.

So - the guestOS just sees a virtual network card and configures to use it just like any real host would - that means the guestOS can take over the IP from a physical host if you aren't careful - just like any machine on the network might.  Also be aware that bridges can be used to snoop on traffic for other VMs/host on the same bridge - so if a more secure network setup is desired, using more bridges and even setting up specific iptables rules to limit traffic may be desired.

---

### Post by Merridion on 2014-09-07
Thank you Doug S & TheFu for the explanation - it helped immensely.

(Sorry for the slow reply/response, had to deal with some unavoidable family issues...)

---

