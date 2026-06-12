---
title: "Dual NIC Ubuntu 11.04 Server - cannot get out to Internet"
date: 2011-07-12
forum: Server Platforms
---

### Post by garyjmellor on 2011-07-12
Hello,
 
I'm hoping someone can assist me with an issue I have with my dual NIC Ubuntu 11.04 server running on my home network. I've recently set this machine up but noticed an issue with Internet connectivity when running 'sudo apt-get update' - it basically fails to get out onto the Internet.
 
The machine actually has three NICs but only eth1 and eth2 are configured. Both are statically configured.
 
eth1 connects to a LAN port on a Netgear DGND3300v2 modem router. This NIC is assigned the IP 192.168.0.4 (the modem router is 192.168.0.1).
 
eth2 connects to a LAN port on a Netgear WNDR3400 router. This NIC is assigned the IP 192.168.1.2.
 
The config for the NICs in /etc/network/interfaces is as follows:
 
auto eth1
iface eth1 inet static
address 192.168.0.4
gateway 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
 
auto eth2
iface eth2 inet static
address 192.168.1.2
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
 
There is also a patch cable going between the router (WNDR3400) and the modem router (DGND3300v2). The router (WNDR3400) therefore picks up the IP 192.168.0.2 from the modem router (DGND3300v2).
 
I'm not a networking expert by any stretch of the imagination - hence this post - but I'm not sure where I'm going wrong.
 
If I take down both NICs with 'sudo ifdown ethX' where X is the NIC to take down, I can get out to the internet on eth2 if I bring it back up with 'sudo ifup eth2'. I can do the 'sudo apt-get update' without a hitch.
 
If I then take down eth2 ('sudo ifdown eth2') and bring up eth1 ('sudo ifup eth1') and then try 'sudo apt-get update' it basically just hangs and/or says there was an issue with communicating with the Ubuntu servers (I don't remember the exact message but essentially it cannot connect to the Internet).
 
If I bring both interfaces up, again I get the same issue as the above paragraph, despite the machine being able to get out to the Internet on eth2 if only this interface is enabled.
 
So, I'm pretty confused. I figure I must have to tell the machine which NIC is for going out to the big wide world on and which NIC is for accessing the LAN side but I don't know how to do this. I've consulted Google for this first before posting here but the answers were for different network setups to mine.
 
I have attached a .jpg of how my network is laid out if this helps in anyway. The machine with the issue is the one labelled E3510.
 
Can anyone tell me what is wrong with my setup or what I need to add to a configuration file (?) in order for me not to have to take down eth1 everytime I need to get out to the Internet on my server using 'wget' or when trying to run 'sudo apt-get update'?
 
One other point to note is that this machine is not always powered up - it is not used a 'pass through' for other machines - it is not intended to control any traffic going through the LAN. It is just a server in its own right currently. I have bigger plans for it once I get the network working on it as I would like.
 
There might well be additional information that is needed but I have put down what I think is enough at this stage. I can always post back with further information if this is needed.
 
I am currently at work at the moment so I would not be able to post back until this evening but I appreciate anyone pointing me in the right direction.
 
Thanks in advance
 
Gary.

---

### Post by SeijiSensei on 2011-07-12
Only the Internet-facing machine should have a "gateway" declaration.  The other interface will simply broadcast packets intended for the other subnet which the machines on that network will read.

The gateway declaration tells the OS where to send packets that have no local destination, so it must be unique.

---

### Post by garyjmellor on 2011-07-15
Hello SeijiSensei,

Thank you for your reply. Unfortunately, it doesn't mean a great deal to me (re: I'm not a network guru by any means). Are you saying I need to make some changes to a file? If so, what file, where and what changes? I want to stop having to unplug NIC#1 just so I can do updates and wget etc. What changes must I make in order for this to happen? I think you might be saying that only eth1 needs the gateway declaration and eth2 should not have the gateway line in at all. Is this correct?

Gary

*~*~*~*~*~*~*
UPDATE:
*~*~*~*~*~*~*
I just amended my NIC#2 entry in /etc/network/interfaces to:

auto eth2
iface eth2 inet static
address 192.168.1.2
#gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

I think that adding # comments the line out. I still get the same error - no connection to the Internet unless I take down eth1 so that requests go out of eth2. Do I need to comment out/remove anything else or am I on the wrong track completely.

Thanks in advance.

---

### Post by hawkmage on 2011-07-15
What do you get for the output of:
```
route -n
```

---

### Post by garyjmellor on 2011-07-16
Hello Hawkmage,
 
route -n gives the following:
 
> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth2
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
0.0.0.0 192.168.0.1 0.0.0.0 UG 100 0 0 eth1
 
The above was run with eth2's gateway commented out in the /etc/network/interfaces file. If I uncomment this, save the changes and restart networking, route -n gives the following:
 
> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth2
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
0.0.0.0 192.168.1.1 0.0.0.0 UG 100 0 0 eth2
0.0.0.0 192.168.0.1 0.0.0.0 UG 100 0 0 eth1
 
I'm sorrry that this information is not tab delimited - I couldn't figure out how to have the tabs respected - it just treated them as white space and collapsed it.
 
Does this help point to the cause of the problem? I don't understand what this information means - especially, 'Metric' and 'Flag' references.
 
Thanks in advance.
 
Gary.

---

### Post by SeijiSensei on 2011-07-16
> **garyjmellor said:**
> I'm sorrry that this information is not tab delimited - I couldn't figure out how to have the tabs respected - it just treated them as white space and collapsed it.

Put the text inside [noparse]```
[/noparse] tags to preserving formatting.

The routing table you posted shows both interfaces with routes for the default route, 0.0.0.0.  As I said, there can be only one of these, and it needs to be the interface that connects eventually to the Internet. I can't tell from the picture in the first post which machine connects to the Internet.  

Is there a "router" like a wifi device between these machines and the Internet, or is one of the Linux machines supposed to be routing out to the Internet?  If the latter, you need to implement "masquerading" on that machine with iptables.  You may also need to enable IP forwarding in the kernel.  If you have a machine that has one interface connected to the Internet (call it eth0), and one pointing at the inside network,
then try this:

[code]
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 123.12.23.43
sudo echo 1 > /proc/sys/net/ipv4/ip_forward

```

Replace 123.12.23.43 with the actual external (Internet) address of the machine.

---

### Post by garyjmellor on 2011-07-17
Thank you for your reply.

I'll try to explain my network setup a little better.

The modem 192.168.0.1 on the picture on my original post is the connection point to the Internet. This is actually a modem router (not sure that makes any difference).

The router 192.168.1.1 is internal to my network. With the exception of the machine marked E3510 (the one I'm having the issue with) and the machine marked G550 everything on the LAN side connects through this directly or through this via the switch.

E3510 needs to see the LAN side and the WAN side, hence two NICs. No machine on my network is routing out to the Internet. If you can imagine the typical cloud icon representing the Internet then this would be coming off the modem 192.168.90.1.

I hope I have made things clearer and not muddied the water further with my understanding of what LAN and WAN are. To clarify my understanding, which you are welcome to correct if I am wrong:

LAN = (Private) everything my side of a connection to the Internet (in this case, everything the router side)

WAN = (Public) everything attached to the modem.

I could be completely wrong but I'm learning all the time :)

I am not able to change the network layout as I've got something specific in mind for which I need this setup so I really need to get the E3510 machine sorted so I don't have to unplug or take down NICs to do what I need.

From your last post "...If you have a machine that has one interface connected to the Internet (call it eth0), and one pointing at the inside network..."...this is what I have with the E3510 machine. eth1 is connecting to the Internet and eth2 is connecting to the inside of the network. If you recall, E3510 is actually a three NIC machine but eth0 is deliberately not configured.

I hope I've clarified my network setup enough for you tell me that this is what I need to do. It certainly sounds like it to me. Could you tell please, what the code actually means and where I need to make the changes? I think it's OK to simply implement a change but it's much better to know what the code means and why it is needed.

Thanks in advance again, I really appreciate the 'hand holding'.

*~*~*~*~*~*~*~*~*
UPDATE
*~*~*~*~*~*~*~*~*
I've just re-read you last post and I think the part where you refer to doing:

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 123.12.23.43
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```...might be for if one of my machines is routing out to the Internet, which isn't the case in my situation. I think 'm a little confused (again).

---

### Post by garyjmellor on 2011-07-18
Given that:[LIST=1]
[*]192.168.0.1 is my modem router - the part that directly connects out the Internet,
[*]192.168.0.2 is my router (LAN side),
[*]192.168.0.3 is the machine mrked G550 in the attachment in my original post,
[*]192.168.0.4 is the IP for NIC#1 in the machine marked E3510
[/LIST]Would I be right in assuming that I would need to change my iptables to the following:
 
 
 
```
 
sudo iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 192.168.0.4
sudo echo 1 > /proc/sys/net/ipv4/ip_forward

```
 
 
Or would it need to be:
 
 
```
 
sudo iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 192.168.0.1
sudo echo 1 > /proc/sys/net/ipv4/ip_forward

```
 
 
I'm not sure whether I need to use 192.168.0.4 (NIC#1's IP) or the IP of the modem router (192.168.0.1).
 
Both cases seem illogical but I perhaps don't understand enough about iptables. I've had a brief reading session but it seems very complex for what I need to achieve. The first example seems to sort of bind eth1 to itself and I'm not sure what the second one is doing other than routing eth1 over the to the modem router. I'm pretty confused. Altering the eth1 NIC in this manner doesn't stop eth2 having a defauly route of 0.0.0.0 either does it? So wouldn't I need to modify this in some way too?
 
Any help gratefully received.

---

### Post by garyjmellor on 2011-07-18
@SeijiSensei:
 
I've just seen another post of yours here [http://ubuntuforums.org/showthread.php?t=1596977](http://ubuntuforums.org/showthread.php?t=1596977)
 
Would this work for me (with modifications that I show further down):
 
--------
 
Let 192.168.1.0/24 be the internal network (eth0) with gateway 192.168.1.1 and 192.168.2.0/24 be the external network (eth1) with gateway 192.168.2.1. You need to use the "ip" command to add these routes:
 
```
ip route add 192.168.1.0/24 dev eth0
ip route add 192.168.2.0/24 dev eth1
ip route add default via 192.168.2.1
```
 
Now traffic for the internal network goes out eth0, and external traffic goes out eth1 via 192.168.2.1.
 
--------
 
I think I would need to change your suggestion to:
 
--------
 
Let 192.168.1.0/24 be the internal network (eth2) with gateway 192.168.1.1 and 192.168.0.0/24 be the external network (eth1) with gateway 192.168.0.1. You need to use the "ip" command to add these routes:
 
```
ip route add 192.168.1.0/24 dev eth2
ip route add 192.168.0.0/24 dev eth1
ip route add default via 192.168.0.1
```
 
 
Now traffic for the internal network goes out eth2, and external traffic goes out eth1 via 192.168.0.1.
 
--------
 
This seems more logical to me.

---

### Post by garyjmellor on 2011-07-18
OK, so I solved this. Nothing complicated at all.

This is my new /etc/network/interfaces file:

```
auto eth1
iface eth1 inet static
    address 192.168.0.4
    gateway 192.168.0.1
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255

auto eth2
iface eth2 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
```All I needed to do was remove the gateway entry for eth2. I previously simply commented this line out with a # character and took the interface down and then back up with ifup/ifdown respectively. For some reason this didn't work - I actually had to remove it.

I'm all happy now. Thanks to everyone who posted with help.

:D

---

