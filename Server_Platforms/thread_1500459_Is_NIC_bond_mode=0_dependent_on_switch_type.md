---
title: "Is NIC bond mode=0 dependent on switch type?"
date: 2010-06-03
forum: Server Platforms
---

### Post by toshko3 on 2010-06-03
I have done a bond with mode=0 and the round robin is working, although I've read that the switch has to support link aggregation/ether channel... I use a plain Ladox 8 port switch for $15 and it works! I use iptraf and bmon to verify that when the traffic comes out and comes in it is balanced. I use 2 NICs and transfer a file from a windows machine to the Ubuntu server and vice versa. All the traffic is balanced and the ifconfig output shows that the traffic flowed through the nics is almost equal and trough the bond0 interface is double. Well it is all OK and seems to be working, BUT wherever I read it is not supposed to work in mode=0 without special support for port aggregation from the switch side. ](*,) The switch is not even manageable and is the cheapest to buy. I'm confused!!!!! I read all the linuxfoundation site info about this and they say that it will not work if there is no support on the switch side!
```
The balance-rr, balance-xor and broadcast modes generally
require that the switch have the appropriate ports grouped together.
The nomenclature for such a group differs between switches, it may be
called an "etherchannel" (as in the Cisco example, above), a "trunk
group" or some other similar variation. For these modes, each switch
will also have its own configuration options for the switch's transmit
policy to the bond. Typical choices include XOR of either the MAC or
IP addresses. The transmit policy of the two peers does not need to
match. For these three modes, the bonding mode really selects a
transmit policy for an EtherChannel group; all three will interoperate
with another EtherChannel group. 
```
```
This mode requires the switch to have the appropriate ports configured for "etherchannel" or "trunking."
```
```
The active-backup, balance-tlb and balance-alb modes do not
require any specific configuration of the switch. 
```
Only for reference: mode=0 is mode=balance-rr.
HELP please!

One more connected question:
What does the cheap switch do when it detects duplicate MACs? Because in this mode the slave interfaces are with the same mac address. What does the switch do when it recieves a packet with the mac address that is duplicated and it is situated in 2 different ports of it? Does it duplicate the packets and sends them on both of the ports OR it randoms the packets through the ports??? If it randoms them the above bond should work because in the end all comes to the bond0 interface. If it doubles them then the traffic shown in the iptraf program should be double for the bond0 interface compared to one interface only used, am I right? The latter I don't see in the iptraf statistics. But in both cases it should work, right? I am so confused! Please someone enlighten me!

---

### Post by toshko3 on 2010-06-07
anyone???):P

---

### Post by toshko3 on 2010-06-16
:confused:

---

### Post by BobVila on 2010-06-16
balance-rr is dependent on having a switch that supports etherchannels.

---

### Post by toshko3 on 2010-07-09
Yeah. But it works with no etherchannel switch. WHY??

---

### Post by toshko3 on 2010-08-04
anyone???

---

### Post by ugmoe2000 on 2011-05-18
I'm sure this issue is long-forgotten but an answer is an answer regardless of whether or not the thread has been dead for a year :P

Anyways the reason it works is because plain-jane vanilla etherchannels like the kind created in the balance-rr mode between the bonded physical interfaces simply divide the traffic across two layer 2 interfaces by some pre-defined means (the round robin algorithm in the case of mode 0).

If you were to use a different mode like perhaps 802.3ad ( mode 4 ) then you would be making use of a special protocol to provide the load-balancing instead of a predefined algorithm... the other side of the link needs to be aware of this because the whole process is negotiated through the use of that additional protocol; it is that protocol (called LACP in mode 4) which is responsible for providing both the splitting up of the traffic and the reconstruction of the traffic across any of the bundled interfaces to create the single logical interface on the other side. Switch awareness is required because the device on the other end of the linux box needs to be able to interpret the protocol which is used to balance the traffic. Since no special protocol is in use for the balance-rr mode the switch requires no special awareness here.

---

### Post by toshko3 on 2011-08-08
First of all, thanks!
Well then every switch is capable of "round-robining" the traffic? 
I really don't know what does a plain basic switch do, when it sees two interfaces, on two ports with the same mac address. Does it do round robin splitting, if I understood? :confused:

---

