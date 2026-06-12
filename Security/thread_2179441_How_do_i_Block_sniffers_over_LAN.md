---
title: "How do i Block sniffers over LAN"
date: 2013-10-08
forum: Security
---

### Post by devraj2 on 2013-10-08
Hiii,

I am new to linux. and i have one security concern with my LAN premises. I have found that some one is sniffing packets over the LAN using free packet sniffing tool.

So, Now i want to block all the sniffing tools like packet sniffer, wire shark, etc..

---

### Post by Kevin_Arnold on 2013-10-08
How did you find out someone is using a packet sniffer? Also, are you using a switched network or wireless?

A switched network is more difficult to sniff, they generally have to do a man in the middle in be able to sniff the traffic. Wireless is an open hub so just make sure it is as secure as possible so they can't get on it.

---

### Post by devraj2 on 2013-10-08
I am using both switched and Wireless network. One of my colleague  had gone through this. I also knows that sniffing is possible in Wireless but is there any possibility to sniff all packets of remote server which is in LAN?

---

### Post by Amorphous Serendipity on 2013-10-08
Hi devraj2,

I don't know your network architecture so I couldn't really provide you with an in-depth answer.

In short, there really isn't a great way to stop passive packet sniffing other than to control your environment.

Some of the best ways to do so would be to:
[LIST=1]
[*]Encrypt all local network traffic (EX: ipsec)
[*]Setup an NAC solution (EX: PacketFence)
[LIST]
[*]Setup Active Directory (if in a Window environment [can be by Linux too]) or another solution like OpenLDAP
[*]Segregate your network with VLANs and setup a guest VLAN that has no access to normal resource.
[/LIST]

[*]Lock down all computers you have control over.
[LIST]
[*]Remove admin rights/rights to install packages/software.
[/LIST]

[*]Never let your Wireless networks touch your LAN (this can be segregated with VLANs).
[/LIST]

The  list goes on. Basically, if you are in control of the computers, lock  them down. If you are worried about guests, your going to want to setup  NAC. Encrypt everything.

---

### Post by devraj2 on 2013-10-09
Thanks [[COLOR=#000000]AhKmNPs[/COLOR]]("http://ubuntuforums.org/member.php?u=1868250"),

here in my LAN area we have implemented different VLAN for all departments and wireless too working in different VLANs. but is there any possibility to sniff encrypted packets of remote server.

---

### Post by Amorphous Serendipity on 2013-10-09
> **devraj2 said:**
> Thanks [[COLOR=#000000]AhKmNPs[/COLOR]]("http://ubuntuforums.org/member.php?u=1868250"),

here in my LAN area we have implemented different VLAN for all departments and wireless too working in different VLANs. but is there any possibility to sniff encrypted packets of remote server.


devraj2,

With passive sniffing, no. You're pretty much just  capturing broadcasts. To sniff packets for remote servers, they would be  doing MITM on one if not a few of the employees (MITM on your entire  network/subnet/vlan CAN be possible, but it would be very noticeable and  also can be a bit of a challenge depending on the network topology). As  for the encryption, yes and no. It would depend on how the server  handles requests (if it's just a website that does ssl redirects than  it's quite easy).

Your best bet is really to lock down your  network so that guests do not have access to corporate resources and  lock down the computers so employees don't have the rights to install  programs that would aid them in packet sniffing. Since you have hardware that is capable of VLANs this should not be that hard and NAC will get you there.

---

### Post by chintan2 on 2013-10-15
I am also facing this kind of issue..do you have any idea to prevent from this kind of attacks MITM attack in LAN area. because i usually found this kind of activity in LAN.

---

### Post by Amorphous Serendipity on 2013-10-17
> **chintan2 said:**
> I am also facing this kind of issue..do you have any idea to prevent from this kind of attacks MITM attack in LAN area. because i usually found this kind of activity in LAN.

chintan2,

There really isn't any 100% foolproof way to stop MITM attacks.

Your best bet is to leverage some sort of NAC solution, to really control who and what is on your network. This will allow you to separate dangerous guests from employees (guests may try to do MITM, but because only guests should be on the guest network, only other guests will be affected [still sad, but at least no employees are affected]).

This isn't 100% and you would still want to lock down the user's computers (restrict what applications are allowed, no admin rights, etc.).

Additionally, any enterprise grade network hardware (Juniper, Cisco, etc), usually has decent protection from MITM (again, not foolproof or an all-in-one answer).

Doing the above should prevent a large portion of it.

---

### Post by public3 on 2013-11-19
Have any free ebooks with more info? I'm developing a website and currently run a webserver so I'm interested in this sort of thing.

I've already locked down ssh and mysql and have IMO a pretty robust firewall rules setup with iptables. But I've never heard of IPsec before.

---

### Post by Lars Noodén on 2013-11-20
IPsec is part of IPv6 also.  If you have the capability (linux end to end) then you might look to see if you can start with IPv6 with IPsec encryption.  You might start here:

[http://www.internetsociety.org/deploy360/ipv6/](http://www.internetsociety.org/deploy360/ipv6/)

If your ISP does not support IPv6 yet, you may opt for a tunnel to avoid waiting.

[http://tunnelbroker.net/](http://tunnelbroker.net/)

---

