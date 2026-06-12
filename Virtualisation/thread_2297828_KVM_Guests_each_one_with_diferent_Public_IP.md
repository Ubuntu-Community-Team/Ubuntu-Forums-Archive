---
title: "KVM Guests each one with diferent Public IP"
date: 2015-10-06
forum: Virtualisation
---

### Post by Delam_Hadz on 2015-10-06
Hi everyone

im having this problem  and im new at ubuntu
 what i want to do is to have Virtual Machines (Virtual Machine Manager is what im using) on an Ubuntu Server with Gui (already have this) but
every VM  should have its unique Public IP Address, i can use 5 in the same cable (eth0) for example the Ubuntu Svr (Host) has the ip 172.33.140.5 and i want the Virtual Machine (Guest) have 172.33.140.6  and so Guest2 .7 Guest3 .8 .

This is the network config i have

auto eth0
iface eth0 inet static
  address 172.33.140.5
 netmask 255.255.255.240
 network 172.33.140.0
 broadcast 172.33.140.15
 gateway 172.33.140.1

auto br0
iface br0 inet static
address 172.33.140.5
 netmask 255.255.255.240
 network 172.33.140.0
broadcast 172.33.140.15
gateway 172.33.140.1 
bridge_ports eth0
bridge stp off
bridge_fd 0
bridge_maxwait 0

i dunno what else can i do , if i need tu search for mac of the Guests and in a file assign them the IP 
Any of your help would be so much appreciate

---

### Post by TheFu on 2015-10-07
BTW, that IP address is a public IP owned by t-mobile.  If they didn't provide it to you, this will never work when connected to the internet.  Most LANs use private IP address spaces, not public ones like this.  172.31.255.255 is the highest IP in the 172.16.x.x range. Ref: [http://www.tcpipguide.com/free/t_IPReservedPrivateandLoopbackAddresses-3.htm](http://www.tcpipguide.com/free/t_IPReservedPrivateandLoopbackAddresses-3.htm)

You  are close, but got some important details wrong in the bridge.
[http://www.dedoimedo.com/computers/kvm-bridged.html](http://www.dedoimedo.com/computers/kvm-bridged.html)
After you clean up  the bridge settings  above ...

Don't use 
```
network 172.33.140.0
broadcast 172.33.140.15
```
Those settings are deprecated.
Also, eth0 should exist, but not be used. The br0 will provide the IP for the VM host.

Inside each VM, setup a static IP, as you like on the same subnet. The  networking for each VM is just like they were physical machines on the network, so the network settings need to match those of the router.

Normally, it is easier to use /24 subnets - 255.255.255.0 is the netmask.  That would allow 254 IPs on the subnet. Doesn't harm anything to use that netmask for a private address space on a LAN.

A complete example file:
```

# ####################################
auto lo
iface lo inet loopback


# ####################################
auto eth0
iface eth0 inet manual

# ####################################
auto br0
iface br0 inet static
  address 172.22.22.6
  gateway 172.22.22.1
  netmask 255.255.255.0
  # mtu 9014
  dns-nameservers 172.22.22.1
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```
Hope this helps.  BTW, manually creating a bridge like this has always been much more stable here than trusting the libvirt generated bridges. I haven't a clue why that is. Manual bridges are fast and solid.

---

### Post by Delam_Hadz on 2015-10-08
Hi man thankx for the advice, I really appreciate that. I used the code on my etc/net/int.. put the eth0 on manual and all that , and i configure a Xp VM Guest manually on Ipv4 Address  and i get Internet and the VM Guest Respond Ping from internet turn off the VMGuest and stops responding , now my doubt : Is there a file where i can put something like this 
[COLOR=#252525][FONT=monospace]01:23:45:67:89:ab  = 172.33.140.6
[/FONT][/COLOR][COLOR=#252525][FONT=monospace]01:23:45:67:89:cb  = 172.33.140.7 
So i can manage from the mac the assigned ip or make all the VM Guest Network Configuration each one

Thanks in advance , and sorry for the answer delay![/FONT][/COLOR]

---

### Post by TheFu on 2015-10-08
To use DHCP reservations, you need a DNS server. Most home routers can do this. 
[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

Only 1 DHCP server is allowed on a network - well, not exactly true, but for you and me, it is FACT.
[B]
BTW you are still using IPs that aren't yours[/B], unless you  work for tmobile.

---

### Post by Skaperen on 2015-10-11
if your public IP address range is *routed* to you over links that have other IP addresses, then you *probably* can use 7 or 8 of the /29 subnet.  i have done so.

---

### Post by TheFu on 2015-10-12
> **Skaperen said:**
> if your public IP address range is *routed* to you over links that have other IP addresses, then you *probably* can use 7 or 8 of the /29 subnet.  i have done so.

Using someone elses' IP range internally can definitely work, but you will not be able to get to their addresses without a multiple other complications. Used to work at a company that used all of 90.x.x.x/8 and  89.x.x.x/8 in addition to 10.x.x.x/8 and all of the 172.16.x.x/16 subnets.  They didn't have much choice and at the time, we didn't have **any** business with those external companies.  Until we did. Then things at the network border got complicated.

For a tiny subnet, there just isn't a good reason to do this - well, there might be 1 - if you work for t-mobile and that is the subnet. Otherwise, it is just asking for difficulties.

I've said my peace.

---

### Post by Delam_Hadz on 2015-10-12
Hi Thanks Again for the advice, im gonna check the link you share but i dont have a DHCP ,i'm connected directly to the internet company Sw and i have that range to use it with the VM Host (the others). I pretend to config this ubuntu server to run like a  DNS Server or a VM guest, im  still thinking about that.  The ips above are just for example.

Anything i let u know.

Thanks!!!! :-)

---

