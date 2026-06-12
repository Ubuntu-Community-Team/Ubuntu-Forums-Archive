---
title: "Ubuntu OpenVPN Gateway - Routing Mutiple Subnets"
date: 2020-12-12
forum: Server Platforms
---

### Post by zaleon46 on 2020-12-12
Hello All,

   I found a good Craft Computing video ([https://www.youtube.com/watch?v=xFficDCEv3c](https://www.youtube.com/watch?v=xFficDCEv3c)) and this other post for virtualbox ([https://mschoofs.blogspot.com/2020/08/vpn-gateway-vm-in-virtualbox.html](https://mschoofs.blogspot.com/2020/08/vpn-gateway-vm-in-virtualbox.html)) on how to setup an OpenVPN gateway for the whole network. I was able to set it up and get everything working on Ubuntu 20.04 LTS, but for my home network I run multiple subnets/VLANS to segregate IoT devices, security cameras, streaming devices etc. off my main network and I'm having trouble getting any of them to pass traffic to the VPN server.

Are there any IPTABLES/ufw gurus here that could help solve this issue?

I thought it might be an easy solution by just adding extra IP subnets to the existing input/out statements then adding some static routes, but that doesn't seem to be the case. Doing this allowed me to ping these subnets from the Ubuntu VPN server, but they still don't pass any VPN traffic!

My current IPTABLES look like this:
```
# Flush all existing settings:
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X

# Block All:
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Allow Localhost communictaion:
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Allow communication with a DHCP server:
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT

# Allow communication within your local network
iptables -A INPUT -s 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -d 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -j ACCEPT
iptables -A OUTPUT -s 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -d 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -j ACCEPT
## Replace this CIDR with your ##

# Allow established sessions to receive traffic:
 iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT

# allow VPN connection
iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment "Allow VPN connection" -j ACCEPT

# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

echo "saving"
echo "done"


```
The only network that is passing traffic to the VPN is the main subnet 10.10.1.0/24 which is also where the Ubuntu VPN server resides.

This is output of route -n where I've added static routes for all the subnets/VLANS I want to pass through the VPN.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.1.1       0.0.0.0         UG    0      0        0 ens192
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 ens192
10.20.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.30.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.40.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.60.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
192.168.5.0     10.10.1.1       255.255.255.0   UG    0      0        0 ens192


```

Also attached[ATTACH=CONFIG]287540[/ATTACH] is a screenshot of the output from iptables -L -n -v

Any suggestions will be greatly appreciated!

---

### Post by darkod on 2020-12-13
I think your problem is that you allow FORWARD traffic only to the tun+ interfaces. When you have multiple home LANs your server is acting like router in a way. The traffic between any of those LANs is considered forwarded.

I'm not sure if your INPUT and OUTPUT cross-network rules would cover this, I have never made such setup. But I think not.

To do a quick test do something like:
```
-A FORWARD -j ACCEPT
```

Make sure that line goes above the -A FORWARD -j DROP because that will drop everything that reached it. Notice how you have dropped packets in FORWARD in the iptales- L -n -v output? My opinion is that drops your cross-LANs packets.

If it starts working with the above temporary rule your will need to focus on allowing the FORWARD traffic cross-LANs.

PS. You also probably need a masquerade rule so that the forwarding works correctly. If your server NIC is ens192 and you are interested only about local traffic (not over the vpn tunnel), it would be something like:
```
sudo iptables -t nat -A POSTROUTING -o ens192 -j MASQUERADE
```

---

### Post by zaleon46 on 2020-12-13
Hi Darko,

   Thanks for your reply. Unfortunately neither one of these changes worked for the other subnets, but 10.10.1.0/24 still continues to work with these changes in place. I also made some other changes as someone posted in the networking forum ([https://ubuntuforums.org/showthread.php?t=2455144](https://ubuntuforums.org/showthread.php?t=2455144)), but they also didn't work. I'm thinking maybe this isn't possible, but it seems weird I can ping the other subnets from the console. However, they will not pass traffic over the VPN still.

---

### Post by volkswagner on 2020-12-14
Is your VPN server currently acting as your “main” router ie: is it already the gateway for your network?

Can you post a diagram of your topology including items that are hyper-visor or virtual machines?

---

### Post by darkod on 2020-12-14
Hold on.

It looked to me like your ubuntu server is connected to all LANs at the same time. So traffic between the LANs wouldn't go over the VPN at all. It would go through the server because it is the central point, but not over the VPN.

What are you trying to achieve actually??

Lets say you have device 10.60.1.20 and it needs to talk to device 10.40.1.20. What is your idea of that communication?

---

### Post by zaleon46 on 2020-12-14
> **volkswagner said:**
> Is your VPN server currently acting as your “main” router ie: is it already the gateway for your network?

Can you post a diagram of your topology including items that are hyper-visor or virtual machines?

Hi Volkswagner, for some devices I set statically the VPN server as the gateway for testing, but currently most devices including DHCP point to my Cisco 3650 switch for their gateway, 10.10.1.1, 10.20.1.1, etc.

I don't think I have a diagram on this computer, but it basically goes Cisco 3650 switch (DHCP server) -> Cisco 5506-X ASA -> Cisco C819G LTE Router -> Internet

There are 2 Cisco 3802i Access Points for wireless and another Cisco 2960G switch in another room connected to the 3650 switch via a trunk line.

All infrastructure is on VLAN10 (10.10.1.0/24), mostly in .1-10 or .250-254. I'm running VMWare ESXi 7 on a filet2 minipc with 4 NICS. The only 2 things running on it currently are a Pihole/Unbound DNS server at 10.10.1.253 and the OpenVPN Gateway on 10.10.1.254. The ESXi itself is on 10.10.1.10

I've also been testing a GL.inet GL-MV1000 for this purpose, but I placed it between the ASA and the LTE router. Unfortunately there it can't see my devices beyond the ASA and won't filter out my work devices MAC addresses from using the VPN like I'd prefer. Beyond that it works fine for the most part. My work computers still seem to work ok even though they're going through a double VPN connection with this setup.

I also tried moving it between the ASA and the 3650 switch, but there it seemed to have the same issue as my own VPN gateway, it could ping stuff but the traffic wouldn't flow out the VPN connection.

---

### Post by zaleon46 on 2020-12-14
> **darkod said:**
> Hold on.

It looked to me like your ubuntu server is connected to all LANs at the same time. So traffic between the LANs wouldn't go over the VPN at all. It would go through the server because it is the central point, but not over the VPN.

What are you trying to achieve actually??

Lets say you have device 10.60.1.20 and it needs to talk to device 10.40.1.20. What is your idea of that communication?

Hi Darkod,

   Well the ultimate goal would be to have a working VPN gateway that all traffic would traverse through except devices I specify or just not point to the VPN server as a gateway. These would include like my work laptops and maybe the 2nd NIC on my desktop computer. Other than those few devices, I'd like everything else to be going through the VPN.

Normally I wouldn't have my network this complicated, but I recently moved to a rural area and the only Internet access choices are satellite or LTE cellular. I chose LTE cellular, but of the big 3/4 companies I've tested, only AT&T seems to not have a hard GB cap where they make the data connection useless, but they do throttle unless I'm VPNing all my traffic so they can't see it.

I don't care much about the devices talking to each other. I'd prefer them not to really, but I do want them all going through the VPN. :)

---

### Post by darkod on 2020-12-14
If you want all traffic over VPN tunnel the general setup you need is:

1). A VPS provider on the internet (your OpenVPN server).
2). A VM on your LAN (your OpenVPN client).
3). In the server.conf on the VPN server you will set it so that clients are forced to use the VPN server/tunnel as default gateway. This way the VM on your LAN will send all its traffic over the tunnel.
4). For all the other computers on the LAN that you want, you set the LAN IP of the client VM as default gateway. That way those computers send all their traffic to that VM, and the VM in turn sends it over the tunnel.

Now because you have multiple subnets you either need to make sure all computers can use the client VM as gateway (either by statis routes or other setup). Or you will need separate client VMs for each subnet.

I think the above is the best layout for this situation.

---

### Post by zaleon46 on 2020-12-14
Darko, that is exactly what I'm trying to do above, but the VPN server (10.10.1.254) is not passing the traffic from the other subnets (10.20.1.0 - 10.60.1.0/24) only the 10.10.1.0/24 subnet it resides on and I'm not sure why.

As for your last setup statement, are you saying I may need a separate VPN server/gateway for each subnet?

---

### Post by darkod on 2020-12-14
Because it is obvious devices from other subnets don't know how to reach 10.10.1.254. That is why it works only from the same subnet.

If you set 10.10.1.254 to be gateway on a computer in different subnet, can you ping 10.10.1.254?

If you can't, that means it doesn't know how to reach it. Because there is no router in between to sort out the routing, you might need vNIC for each subnet on your VPN gateway VM. That way each computer from 10.20-10.60 will be able to reach it and things should work out after that.

Either this, or separate VPN gateway in each subnet.

---

### Post by SeijiSensei on 2020-12-14
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.1.1       0.0.0.0         UG    0      0        0 ens192
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 ens192
10.20.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.30.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.40.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.60.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
192.168.5.0     10.10.1.1       255.255.255.0   UG    0      0        0 ens192
```

What machine is this? 10.10.1.254?

Does 10.1.1.1 have separate interfaces in 10.20.1.0/24, 10.30.1.0/24, etc.?  If not, it's going to send any traffic to those networks out its default gateway. 

I don't use things like VLANs so maybe I'm all wet here. If I were going to build a router for all those networks, I'd put it in 10.0.0.0/8. Segmenting the network with /16's like 10.10, 10.20, etc., seems overly complex. I'd use a /16 like 10.10/16 with /24 subnets like 10.10.1.0/24, 10.10.2.0/24, etc., but that's just me. 

Still the router would need to have interfaces in 10.10.1.0/24, 10.10.2.0/24, etc. There are ways to assign virtual interfaces to an ethernet port (using eno1:0, eno1:1, etc.), but I'm not sure how you'd number both the physical port and the subnet virtual ports. Maybe

eno0 -> 10.10.0.1/16
eno0:0 -> 10.10.1.1/24
eno0:1 -> 10.10.2.1/24
etc.

Just something to consider.

I'd disconnect this network from the public Internet and pull down the firewalling rules until you can ping hosts across the networks. For instance, can 10.20.1.37 ping 10.40.1.23? Can they all ping 10.10.1.1.  Until you get all the routing working properly, firewalling rules make it hard to know where the problems lay.

---

### Post by zaleon46 on 2020-12-15
Thanks for your suggestions and assistance. Sounds like it is getting  complex to fix and might be easier to do with an actual router or routing OS  like Pfsense/OPNsense/OpenWRT so I may try that first.

---

### Post by SeijiSensei on 2020-12-15
I think you need to figure out the best addressing scheme first. How many subnets? Why that many? Why must their hosts be on separate networks?

---

### Post by darkod on 2020-12-16
On top of what Sensei says about the subnet planning I would like to remind you that you would have similar problem even with dedicated router (physical or virtual).

Your intention to send all traffic is best done with dedicated VM to serve as VPN gateway. Since you say you have your own ESX this is easily done.

The only thing you need to do is assign vNICs in this VM for each subnet. So your VPN gateway will have IPs like 10.10.1.254, 10.20.1.254, 10.30.1.254, etc in each corresponding subnets. That way it communicates to all devices in all subnets.

And your devices in turn, depending in which subnet they are, will have as gateway 10.10.1.254, 10.20.1.254, 10.30.1.254, etc accordingly.

If you VPN Gateway VM is still not configured for routing, this is easy to do. And it is also easy to set it to send all traffic over the VPN tunnel.

That is all you will need to do and it will be much easier with such VM then with dedicated router which still will need to be connected to all subnets and you will also need to configure it to send all traffic over the VPN tunnel.

---

### Post by zaleon46 on 2021-01-01
> **darkod said:**
> On top of what Sensei says about the subnet  planning I would like to remind you that you would have similar problem  even with dedicated router (physical or virtual).

Your intention to send all traffic is best done with dedicated VM to  serve as VPN gateway. Since you say you have your own ESX this is easily  done.

The only thing you need to do is assign vNICs in this VM for each  subnet. So your VPN gateway will have IPs like 10.10.1.254, 10.20.1.254,  10.30.1.254, etc in each corresponding subnets. That way it  communicates to all devices in all subnets.

And your devices in turn, depending in which subnet they are, will have  as gateway 10.10.1.254, 10.20.1.254, 10.30.1.254, etc accordingly.

If you VPN Gateway VM is still not configured for routing, this is easy  to do. And it is also easy to set it to send all traffic over the VPN  tunnel.

That is all you will need to do and it will be much easier with such VM  then with dedicated router which still will need to be connected to all  subnets and you will also need to configure it to send all traffic over  the VPN tunnel.

Hi darkod,

  After taking a break for the holidays and working on some other  projects, I decided to mess with this again. So I think I fixed my main  problem in that the VLANS weren't routing correctly from the VMWARE host  due to the port not being set as a trunk port on the switch.

I reset all this up from scratch and it works fine from VLAN10 (my main  vlan), but when I test with other VLANs, they're showing up as my ISP's  public IP address instead of the VPN IP address. So I feel like i'm  getting further as nothing would work previously from other VLANs, but  the gateway appears to not want to route the other VLANs across the vpn  tunnel.

I thought maybe I did need to setup an interface for each VLAN as you  suggested above for it to route correctly. The above setup that  partially works was with a single interface (ens160) in netplan. When I  added the other 6 VLANs to the netplan with their own interface  10.20.1.254, 10.30.1.254, etc. the OpenVPN connection started using the  last NIC (ens256, 192.168.5.254) in the list and now nothing works.

So I guess if I leave those other interfaces configured, how do I set  OpenVPN to use the main VLAN10 interface (ens160) again? And how do I  make sure all traffic is routed across the VPN tunnel?

This is my netplan file:
```
 ens160:
      dhcp4: no
      addresses: [10.10.1.254/24]
      gateway4: 10.10.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
 ens161:
      dhcp4: no
      addresses: [10.20.1.254/24]
      gateway4: 10.20.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.20.1.252, 10.10.1.252]
 ens192:
      dhcp4: no
      addresses: [10.30.1.254/24]
      gateway4: 10.30.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
 ens193:
      dhcp4: no
      addresses: [10.40.1.254/24]
      gateway4: 10.40.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
 ens224:
      dhcp4: no
      addresses: [10.50.1.254/24]
      gateway4: 10.50.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
 ens225:
      dhcp4: no
      addresses: [10.60.1.254/24]
      gateway4: 10.60.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
 ens256:
      dhcp4: no
      addresses: [192.168.5.254/24]
      gateway4: 192.168.5.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
```

And my IPTABLE rules:
```
#!/bin/bash
# Flush
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X

# Block All
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# allow Localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Make sure you can communicate with any DHCP server
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT

# Make sure that you can communicate within your own network
iptables -A INPUT -s 10.0.0.0/8 -d 10.0.0.0/8 -j ACCEPT
iptables -A OUTPUT -s 10.0.0.0/8 -d 10.0.0.0/8 -j ACCEPT

# Allow established sessions to receive traffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT

# allow VPN connection
iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment "Allow VPN connection" -j ACCEPT

# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

# Log all dropped packages, debug only.

iptables -N logging
iptables -A INPUT -j logging
iptables -A OUTPUT -j logging
iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7
iptables -A logging -j DROP

echo "saving"
iptables-save > /etc/iptables.rules
echo "done"
```

---

### Post by darkod on 2021-01-03
I assume all ensXXX are correct, all those interfaces exist inside the VM and their names are correct, right?

When using multiple NICs don't put gateway and dns on the additional NICs. Only have gateway and nameservers on the ens160 interface. For the rest you just need the dhcp OFF parameter and the address parameter (which includes the netmask itself).

Try it like that.

First take care of that and we will talk next steps. Throwing too much information at once makes it harder to follow it. :)

---

### Post by zaleon46 on 2021-01-03
> **darkod said:**
> I assume all ensXXX are correct, all those interfaces exist inside the VM and their names are correct, right?

When using multiple NICs don't put gateway and dns on the additional NICs. Only have gateway and nameservers on the ens160 interface. For the rest you just need the dhcp OFF parameter and the address parameter (which includes the netmask itself).

Try it like that.

First take care of that and we will talk next steps. Throwing too much information at once makes it harder to follow it. :)

Yes, that is correct. All the ensXXX entries are the different NICS. Not sure why it doesn't number them in sequential order but at least they work.

I've removed the gateway and name servers from the other NICs, so OpenVPN is defaulting to VLAN10 again.

My netplan now looks like this:

```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens160:
      dhcp4: no
      addresses: [10.10.1.254/24]
      gateway4: 10.10.1.1
      nameservers:
         search: [home.internal]
         addresses: [10.10.1.252, 10.20.1.252]
    ens161:
      dhcp4: no
      addresses: [10.20.1.254/24]
    ens192:
      dhcp4: no
      addresses: [10.30.1.254/24]
    ens193:
      dhcp4: no
      addresses: [10.40.1.254/24]
    ens224:
      dhcp4: no
      addresses: [10.50.1.254/24]
    ens225:
      dhcp4: no
      addresses: [10.60.1.254/24]
```

---

### Post by darkod on 2021-01-03
OK. So next step is to confirm that the VPN gateway VM goes out over the VPN tunnel. You can do that using the following command:
```
curl icanhazip.com
```

The public IP it shows should be the public IP of the VPN server where you are connecting to.

If that part works OK, next you need to test from a machine from one of the secondary subnets. On that machine set the default gateway to be 10.X.1.254 and then check its public IP. It should also show the public IP of the VPN server. That means the traffic is going over the VPN tunnel.

---

### Post by zaleon46 on 2021-01-03
> **darkod said:**
> OK. So next step is to confirm that the VPN gateway VM goes out over the VPN tunnel. You can do that using the following command:
```
curl icanhazip.com
```

The public IP it shows should be the public IP of the VPN server where you are connecting to.

If that part works OK, next you need to test from a machine from one of the secondary subnets. On that machine set the default gateway to be 10.X.1.254 and then check its public IP. It should also show the public IP of the VPN server. That means the traffic is going over the VPN tunnel.

Yes, I tested this earlier and should have mentioned it. It is slightly worse than before in my opinion. So everything works fine if I'm on a 10.10.1.x/24 address and pointing to 10.10.1.254 as the gateway it shows up as the VPN public IP. However, currently if i use any other VLAN like 50 or 20 and point them to 10.50.1.254, 10.20.1.254 etc. I have no Internet access. Even if i point them to 10.10.1.254 I still have no internet access on those subnets/VLANs.

Before I removed the gateway and nameservers from the netplan config, I would have internet access on those VLANs, but it would show as my ISP's public IP instead of the VPN's public IP.

---

### Post by darkod on 2021-01-03
You had internet access because there were going out over the ISP router. Now it doesn't work because something is blocking that connection. Most probably the iptables rules.

I would start with much simpler iptables rules (basically almost allow everything) and then start introducing restrictions. That way you also know which iptable rule made the traffic flow stop.

The VPN gateway is a VM in your home network. Such strict iptables rules are really not necessary. This is not a server exposed to the internet in any way.

For example, these lines are not necessary in your list, they don't do anything relevant, only can create problems:
```
# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP
```

---

### Post by zaleon46 on 2021-01-03
Well even if i flush all the iptables and run "sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward", the VPN will connect but I can't connect to anything on the internet if i'm pointing to 10.10.1.254.
These are my iptables -L which I assume means they're empty and the default policy applies to accept all traffic?
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Maybe it is a routing issue instead? These are the results of ip route show:
```
0.0.0.0/1 via 10.8.1.1 dev tun0
default via 10.10.1.1 dev ens160 proto static
10.8.1.0/24 dev tun0 proto kernel scope link src 10.8.1.5
10.10.1.0/24 dev ens160 proto kernel scope link src 10.10.1.254
10.20.1.0/24 dev ens161 proto kernel scope link src 10.20.1.254
10.30.1.0/24 dev ens192 proto kernel scope link src 10.30.1.254
10.40.1.0/24 dev ens193 proto kernel scope link src 10.40.1.254
10.50.1.0/24 dev ens224 proto kernel scope link src 10.50.1.254
10.60.1.0/24 dev ens225 proto kernel scope link src 10.60.1.254
128.0.0.0/1 via 10.8.1.1 dev tun0
185.93.XXX.XXX via 10.10.1.1 dev ens160

```

---

### Post by darkod on 2021-01-03
The ip_forward needs to be allowed in /etc/sysctl.conf. Permanently!!

I'm not familiar what that sudo command does, maybe it does the same, but I have always did it by editing /etc/sysctl.conf to allow ipv4 ip_forward. So check it and in case you modify the file restart the VM to apply the change after you modify it. You do it only once and then it remains configured.

Also, did you configure the OpenVPN server to force the client to use the tunnel as default gateway? The routes look OK, so that part might be OK.

Post the output also of:
```
sudo iptables -t nat -L -n -v
```

---

### Post by zaleon46 on 2021-01-03
Yes, ipv4 ip_forward=1 is in the /etc/sysctl.conf and uncommented still. It is also set using the sudo command in the iptables bash script, but I currently have to run that manually since I didn't implement the service part of it as the other VLANS aren't working. The original post with the links suggested putting it in a bash script so that it can be easily disabled for troubleshooting like this.

I found this article on Hidemyass's VPN support site ([https://support.hidemyass.com/hc/en-us/articles/202721486-Using-Linux-Virtual-Machine-instead-of-a-router-for-VPN](https://support.hidemyass.com/hc/en-us/articles/202721486-Using-Linux-Virtual-Machine-instead-of-a-router-for-VPN)) that uses simpler iptable rules, but the results were the same with it. My main VLAN10 (10.10.1.254) has internet access under the VPN's public IP, but the other VLANS have internet access with the ISP's public IP. That is why I thought it might be a weird routing issue.

This is the output of sudo iptables -t nat -L -n -v
```
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

```

I'm using a commercial VPN provider (Nord and OVPN) so I can't control their server.

---

### Post by darkod on 2021-01-03
You have no masquerade rule.

Try this and it should make it work for subnet 10.10.x.x:
```
sudo iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
sudo iptables -t nat -A POSTROUTING -o ens160 -j MASQUERADE
```

If that works, you will need to add MASQUERADE rule like the second line for each ensXXX interface on the VPN gateway. After that it should work for all subnets.

---

### Post by zaleon46 on 2021-01-03
That works for ens160, but adding it to the other interfaces has no effect. If I point them to the respective IP of the gateway (10.20.1.254, 10.30.1.254, etc.) they have no internet connection. If i point them to 10.10.1.254 instead,they have an internet connection, but it showing the ISP public IP address instead of the VPN public IP as when testing from a 10.10.1.xxx address.

---

### Post by darkod on 2021-01-04
Sounds like you might have errors in your complex situation with VLANs. Or I am missing something of this setup.
Lets say you have a machine 10.20.1.20/24. Does ping to 10.20.1.254 work at all?
You say no internet with 10.20.1.254 but yes with 10.10.1.254. The thing is that 10.20.1.0/24 being in its own subnet in its own isolated VLAN, then that machine should not even be able to reach 10.10.1.254. How does it get there?
Look at the time and energy you use on this. You need to reconsider again whether you need all these VLANs and subnets. Can't you make a simpler setup? You would make it work much faster with simpler setup design.
Things are not working correctly for you. The above example of devices from other subnets being able to reach 10.10.1.254 is a clear example. If they are really isolated VLANs that shouldn't happen.

PS. You opened this thread for OpenVPN but right now I would focus more on your VLANs config and how all of that works. As you can see, the VPN is working as expected for the 10.10.1.0/24 subnet. That shows you the configuration is correct more or less. It doesn't work for the other subnets/VLANs but that looks more related to VLANs and networking, then to VPN config.

---

### Post by SeijiSensei on 2021-01-04
First thing I would do is install the now-deprecated traceroute package

```
sudo apt install traceroute
```

Then run commands like 
```

traceroute 10.10.1.254
traceroute 10.20.1.254
traceroute 8.8.8.8

```
from machines on different subnets and see how far you get and where traffic is blocked.

---

### Post by zaleon46 on 2021-01-04
Well I decided to start with the VM servers and found I can't ping any  of the gateways or other IPs from the VPN server. As shown in the  attached, the left server is my VPN server and the right is my  AdGuard/DNS server.
[ATTACH=CONFIG]287685[/ATTACH]

After discovering this I decided to rebuild the VPN server since its a VM anyway and I found that the ping issues start occurring when I add the other 6 NICs and assign them an IP address in netplan then I can't ping anything on the other VLANS after that. I get the destination unreachable message.

I don't have any problems with my 2 AdGuard/DNS servers, every device on every subnet can communicate with them, but they also only have 1 NIC/IP Address assigned to them.

The VPN server works with 1 NIC/IP assigned to the server and I can point other VLAN devices to it, but they don't get routed over the VPN. Like if I'm on 10.30.1.92/24 and point it to 10.10.1.254 as the gateway, I have network and internet access, but if I go to whatismyipaddress.com it shows my public ISP ip address instead of the VPN.

I will keep testing and see if I can figure out where the failure is until I give up and go back to the resource hog of Windows ICS. :)

---

### Post by zaleon46 on 2021-01-05
So after rebuilding servers from scratch, testing on Ubuntu and Windows, I don't it is possible to have 1 VPN server for multiple subnets or VLANS. Both Linux and Windows exhibit the same behavior, the subnet/vlan the server is on works fine routes out the VPN tunnel, but the other subnets/vlans don't route out the VPN tunnel and show up as the ISP public IP address.

I think my particular setup will require VPN server on each VLAN in order for all traffic to be routed through a VPN tunnel.

I appreciate you guys help and knowledge in this area. I was hoping we could make it work, but I don't think its possible with my current network infrastructure.

---

### Post by darkod on 2021-01-06
IMHO you have some other issue in this situation. VPN gateway on each VLAN should not be necessary because one vNIC in each VLAN does the same job. So you can have one single VPN gateway VM with vNIC in each VLAN.

If you can't make that work, then you probably won't be able to make it work with multiple VPN gateways. Because the principle is the same.

The bottom line is you need to direct the devices on each VLAN to use corresponding IP as gateway. Wheter that gateway is only a vNIC or completely separate VM is besides the point.

I don't know how knowledgeable you are about creating networks and VLANs, but you have to look for the problem there. And again I repeat, especially seeing how many issues you have to make it work, rethink your network/VLAN design. Doing a simpler design will help you a lot.

I don't know your circumstances but talking about 6 VLANs for home setup sounds excessive. I have worked in small companies where the computer network didn't need so many VLANs. Sometimes you read something about traffic isolation and it sounds like good idea on paper so you start implementing it without second thought, but at the end of the day for home setups such strict isolation is rarely needed.

---

