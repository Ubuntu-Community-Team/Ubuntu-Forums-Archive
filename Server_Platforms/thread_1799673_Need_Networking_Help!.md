---
title: "Need Networking Help!"
date: 2011-07-07
forum: Server Platforms
---

### Post by That Guy Is Here on 2011-07-07
Hi all,

I need some help. I Have three Ubuntu servers that I had connected to my router (Linksys WRT54G V 8.2). Well then I ran out of ports so I bought a  Netgear FS108 switch. So my current set up is Modem---->Router---->Switch---->Ubuntu Servers. My problem is that it cant connect to the internet. Do I need a cross over cable? Or am I doing something else wrong?

---

### Post by arrrghhh on 2011-07-07
Is the router handing out DHCP leases, or are you using a static IP configuration?

Can you ping out to an IP?  ```
ping 8.8.8.8
```

The servers can see eachother I assume since your concern seems to be internet-only?

---

### Post by doas777 on 2011-07-07
is it a managed/smart switch? if so, make sure it doesn't have a DHCP server running.
I would recommend powercycling the cablemodem and router, for a quick test.

if that doesn;t work, on one of the servers, run these commands and post back the output.
```

sudo ifconfig -a
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf
nslookup www.ubuntuforums.org
route 

```

---

### Post by That Guy Is Here on 2011-07-08
> **arrrghhh said:**
> Is the router handing out DHCP leases, or are you using a static IP configuration?

Can you ping out to an IP?  ```
ping 8.8.8.8
```

The servers can see eachother I assume since your concern seems to be internet-only?
The server I have running has a static IP. When I pinged out 8.8.8.8 or google.com, it gave the error
```

connect: Network is unreachable

```


> **doas777 said:**
> is it a managed/smart switch? if so, make sure it doesn't have a DHCP server running.
I would recommend powercycling the cablemodem and router, for a quick test.

if that doesn;t work, on one of the servers, run these commands and post back the output.
```

sudo ifconfig -a
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf
nslookup www.ubuntuforums.org
route 

```

Ok well I googled it, found the manual and no it is not a smart/managed switch.

Ok sudo ifconfig -a
```

eth0         Link encap:Ethernet  HWaddr 00:14:22:5a:45:21
             BROOADCAST MULTICAST MTU1500 METRIC:1
             RX packets:0  errors:0 dropped:0 frame:0
             TX packets:0  errors:0 dropped:0 carrier:0 
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
             Interrupt:16

lo           Link encap:Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436 Metric:1
             RX packets:8  errors:0 dropped:0 frame:0
             TX packets:8  errors:0 dropped:0 carrier:0 
             collisions:0 txqueuelen:1000
             RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
                              


```

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

iface lo inet loopback

iface br0 inetstatic
  address 192.168.1.101
  netmask 255.255.255.0
  gateway192.168.1.1
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
        
iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down iplink set $IFACE down promisc off

```

sudo cat /etc/resolv.conf

```
nameserver 8.8.8.8
nameserver 8.8.4.4
domain nc.rr.com
search nc.rr.com
```

nslookup [www.ubuntuforums.org](www.ubuntuforums.org)

```
;; connection timed out; no servers could be reached
```

route

```
Kernel IP routing table
Destination            Gateway         GenMask         Flags Metric Ref        Use Iface
```

---

### Post by arrrghhh on 2011-07-08
I guess I'm confused by your /etc/network/interfaces file...  What do you have br0 for?  Why doesn't eth0 have an IP?  I also don't see br0 in ifconfig...

---

### Post by That Guy Is Here on 2011-07-08
Br0 was for a VPN that never worked/was set up. I plan on reinstalling the OSes later but want to make sure the network works first. br0 probly doesnt show up because it was never configured correctly

---

### Post by boblizar on 2011-07-08
sudo cat /etc/resolv.conf

Code:

nameserver 8.8.8.8
nameserver 8.8.4.4
domain nc.rr.com
search nc.rr.com

 is your problem....

you need to have your computer query a DNS server.  its probably also your "gateway"

192.168.1.1 instead of 8.8.8.8 && 8.8.4.4

no dns = no net = bad routes = bad querys = google not found

load up terminal

alt + f2

run > gnome-terminal

```

sudo su

```
&&
```

rm /etc/resolv.conf
cat > /etc/resolv.conf << "EOF"
nameserver 192.168.1.1
EOF
exit

```

press enter to exit root mode then try

ping -c 5 192.168.1.101

if success

ping -c 5 192.168.1.1

if success

ping -c 5 [www.google.com](www.google.com)

and by then you should be good to go

--------------------------------------------if my solution is not working to return your system back to where it was----------------------------------------------------

```

sudo su

```
&&
```

rm /etc/resolv.conf
cat > /etc/resolv.conf << "EOF"
nameserver 8.8.8.8
nameserver 8.8.4.4
domain nc.rr.com
search nc.rr.com
EOF
exit

```

press enter to exit root mode

-----------------------------side note----------------------
Router---->Switch---->
i have piggy backed switches, wrt54g-tm with linux to be exact
you can have the router use its standard out to go into the "switch(thats really the wrt router)" internet port

i would use pings to and from 192.168.1.* subnet computers to eachother first and pings to the 192.168.1.1 to diagnose whats going on.

i would also make sure that your router is using something other than 192.168.1.* subnet to prevent redundancy in the chain and introduce confusion to the switch.  i would set the router to run 10.0.0.* ip addresses and use the 192.168.1.* for the LAN.

---

### Post by arrrghhh on 2011-07-08
You'll also need to flesh out the IP configuration for eth0.  That's not correct...  Do all your servers have this same config?  I wouldn't think you would be able to access other machines on the LAN, let alone the internets.

---

### Post by That Guy Is Here on 2011-07-08
No it didnt work. And like I said before Im reinstalling all the OSes. So I got one started and when it got to the DHCP part it said the configuration failed. So something else is wrong not just the server.


Edit: Also when I connect a laptop directly into the switch I get no internet access either

---

### Post by arrrghhh on 2011-07-08
> **That Guy Is Here said:**
> No it didnt work. And like I said before Im reinstalling all the OSes. So I got one started and when it got to the DHCP part it said the configuration failed. So something else is wrong not just the server.


Edit: Also when I connect a laptop directly into the switch I get no internet access either

Are you not running static then?  You are using DHCP?  Do you have a DHCP server?

---

### Post by That Guy Is Here on 2011-07-08
On the machine trying to reinstall the os, no. But on the machine I gave the output of, yes. I am using DHCP and my DHCP server is my router.

---

### Post by arrrghhh on 2011-07-08
> **That Guy Is Here said:**
> On the machine trying to reinstall the os, no. But on the machine I gave the output of, yes. I am using DHCP and my DHCP server is my router.

Ah... how is the switch connected to the router?  On a LAN port on the router using a straight thru cable?

I believe that connection is your problem.  I believe you need a crossover cable between these devices...  

Assuming that is just flat out wrong, have you tried configuring it statically instead of depending on DHCP?

---

### Post by Rakeshvijayan on 2011-07-08
please conform your gateway from your ISP and  check the strait crimping  is correct form switch to server

---

### Post by Rakeshvijayan on 2011-07-08
> **arrrghhh said:**
>  that connection is your problem.  I believe you need a crossover cable between these devices...  
  

same device need the cross over .... dhcp from  router is not a problem if you using static Ip .did you check directly through the router ? and correct the ip range

---

### Post by kevinthecomputerguy on 2011-07-08
Boot off a ubuntu live cd.
If the problem = solved, then problem = that computer.
If the problem = not solved, then the problem = networking.

---

### Post by That Guy Is Here on 2011-07-08
Ok but heres the problem, on the manufacturer's site it say specifically not to use a cross over cable because it is autosensing.

---

### Post by doas777 on 2011-07-08
I don't think that your switch uplink is your issue, as most modern switches can remap pinouts to match whatever cable is provided, and because IS-IS connections usually use patch cable, and IS-ES connections use crosspatch.
lets start with software troubleshooting.

your interface file appears to be the issue.
under eth0, set it up like one of the examples here:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

then restart networking:
```
sudo /etc/init.d/networking restart
```, and see if you have an ipv4 address for eth0 in ifconfig -a.

---

### Post by Rakeshvijayan on 2011-07-08
> **That Guy Is Here said:**
> Ok but heres the problem, on the manufacturer's site it say specifically not to use a cross over cable because it is autosensing.
Try kevinthecomputerguy side .....and post the result []("http://ubuntuforums.org/member.php?u=1013263")

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
Actually, if i remember, Cross-over was only Computer-Computer, not Switch-Router. Try changing to a patch cable and see if that works. Also, have you tried to ping you router and can you connect to it? And from what i've read, your using two DHCP servers? Thats not right, your only gonna need one, unless you have seperate subnets.

---

### Post by Drenriza on 2011-07-08
I would say, depending on what you use your servers for. Then you need a semi-profession equipment, because home routers / switches like those you buy in your normal consumer store, aren't very good at debugging or handling traffic.

Get some better equipment at ebay.com. Here you can get fair priced Cisco equipment and it would probably suit your needs a lot better.

If you should decide to go Cisco, your welcome to pm me about help with configuring your device, through the CLI.

GL

EDIT:
The deal with cross-over and straight through cables, is not important. All decent routers, switches and NIC,s has build-in detection and compensation to see what type the cable is,
and add adjustments so the system can use it. No matter what type it is.

---

### Post by arrrghhh on 2011-07-08
> **headvampyre@hotmail.co.uk said:**
> Actually, if i remember, Cross-over was only Computer-Computer, not Switch-Router. Try changing to a patch cable and see if that works. Also, have you tried to ping you router and can you connect to it? And from what i've read, your using two DHCP servers? Thats not right, your only gonna need one, unless you have seperate subnets.

Crossover is for switch-to-switch as well.

Switch-to-router normally just works as others have stated.  Sorry for derailing ;).

---

### Post by That Guy Is Here on 2011-07-08
Ok well I figured out one of the problems, I had my switch in a closet that I installed two in wall ethernet ports. So when I took it out and pluged my switch into a different port in my living room, I could connect to the internet on one of my laptops. So I thought maybe if I just switch the ports for the closet on the router under the house it would work, just as the one in the living room did.....No it didn't. So now Im stuck trying to figure out whats wrong with the cords.

---

### Post by Rakeshvijayan on 2011-07-08
make me so confusing .......don't be panic, I think I can help you to resolve this issue .


First let me know  about your  cable  connection {strait or crossover}  modem to switch and pc

---

### Post by That Guy Is Here on 2011-07-08
Its all strait cables. My switch has auto uplink which auto sorts the connections so removes the need for a crossover cable.

---

### Post by msandoy on 2011-07-09
Your setup should be like this, Modem -> WAN port on Router. LAN port on router -> LAN port on switch. All available LAN ports can then be used for servers/desktops, and the router will take care of the DHCP system. No need for fancy cables here, ordinary network cables will do all over. This switch does not have DHCP, this is why you have no IP address on any of the machines connected to it. Do not use the uplink port, use one of the LAN ports to connect router and switch.

---

### Post by That Guy Is Here on 2011-07-09
Hi guys, I just wanted to say thanks to you all for all your help. I fixed it, I just replaced the end of the cable and now it works! :)

---

