---
title: "trouble setting up VLAN between linux and L3 switch"
date: 2013-04-09
forum: Server Platforms
---

### Post by nicolasdiogo on 2013-04-09
hello,

i am trying to setup 4 linux system to connect.

while using non-tagged (default) network works fine.

when i try to setup a vlan it fails _miserably_..

the switch is a CISCO sg300 series.
all ports are set as TRUNK - i thought this would enable all traffic to be able to flow through these (tagged and non-tagged)

the default network (non-tagged) has network mask:
192.168.1.0/24

and the tagged vlan 10 has network mask:
10.0.10.0/24

on the linux, i have setup as:
[I]
boxA1 - br0 - non-tagged
boxA2 - br0 - non-tagged
boxB1 - br10 - vlan 10
boxB2 - br10 - vlan 10[/I]

the trouble is that i can not connect boxes:
[B]boxB1
boxB2[/B]

using the vlan network.

for instance, in boxB1 i try to connect via ssh using the IP:
[B]
ssh thisuser@10.0.10.3[/B]

but that times out. and **tracepath** or **nmap** can not even find another host on the tagged network.

any suggestion on how to proceed.

P.S.: i am really lost on this topic

---

### Post by darkod on 2013-04-09
If this are not VMs, how about trying without bridging? Something like bond0.10 or even without bonding first, just to make sure it works with the VLAN. So, it would be something like eth0.10.

---

### Post by nicolasdiogo on 2013-04-09
thanks Darkod,


i have my 2 testing systems (boxB1, boxB2) using a very simple vlan setup, with a single Ethernet connection (eth0) with a single vlan tagged 10 (eth0.10)

trouble is that i can not tracepath to each other - and not even get tracepath to the switch.

i really appreciate your assistance and guidance here - but i am a proper newbee on these subject.

thanks

---

### Post by darkod on 2013-04-10
If you are using a single cable, why setting all the ports of the switch to trunk? I don't know much about cisco, except that they tend to complicate things that are really very simple. If you have all ports set to trunk(s) I'm not sure how it would like a non-trunked connection, which is a single cable. Your problem might be on the switch side.

---

### Post by nicolasdiogo on 2013-04-10
Hello Darko,

once again you are right - i will stop doubting your knowledge!..

i have got properly confused while configuring the switch as i failed to understand the CISCO way of thinking.

this discussion sort of clarified things for me (mainly that i am not alone in misunderstanding CISCO).
[https://supportforums.cisco.com/message/3396657](https://supportforums.cisco.com/message/3396657)


the fact is that even with the ports set as TRUNK, it is necessary to specify the VLAN that will be carried through as the default is to drop tagged traffic (at least that is the behaviour that i observed)

the other important aspect is that if you choose to have these ports to be TAGGED (default is UNTAGGED), ANY traffic that originates from a non-tagged port will not access these TAGGED ports.

**in a nutshell, i had to define the VLANs, add these to the relevant ports, and make sure that these were untagged ports.**

thanks a lot for your guidance with these network problems.


regards,


Nicolas

---

