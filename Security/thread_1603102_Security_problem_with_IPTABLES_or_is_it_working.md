---
title: "Security problem with IPTABLES or is it working?"
date: 2010-10-22
forum: Security
---

### Post by johnkills on 2010-10-22
Steps..
**_Install_:**
Wireshark
tcpreplay

**1. Open Wireshark**

Open it and do some web browsing or anything on the internet then save the file as normal.pcap

**2.Lock your computer for ALL incoming and ALL outgoing packets.**

sudo iptables -P OUTPUT DROP
sudo iptables -P INPUT DROP

_**Nothing**_ is supposed to come and go with those rules. Your computer is locked. 
[B]
3.Open wireshark again[/B]
Try doing anything online, it wont work. No packets are shown in wireshark because iptables blocked everything. 
[B]
4.tcpreplay[/B]

If you use tcpreplay to send packets of a file ...

sudo tcpreplay  --intf1=eth0 normal.pcap

You can see on wireshark packets coming and going! My guess is that packets dont really go outside of your computer but I dont know that. They probably only show on wireshark but why? I thought iptables would block everything if everything is locked. 

Anyone can tell me what is happening and why iptables let wireshark see any packets? 

Thanks

---

### Post by The Cog on 2010-10-22
I haven't tried it, but my guess is that the packets really are going out on the LAN. It would appear (from your description) that tcpreplay gains access to the interface at some point outside of the connection from the IP stack to iptables. 

I don't think it is really a security issue though. Anyone who can use **sudo tcpreplay** can also use **sudo iptables** too.

---

### Post by johnkills on 2010-10-22
> **The Cog said:**
> 
I don't think it is really a security issue though. Anyone who can use **sudo tcpreplay** can also use **sudo iptables** too.

True :) 

I tried using tcpreplay with a normal user and it seems it cant access eth0.. so tcpreplay wont work. I wonder if there is ever a situation where a user that cant sudo or is a root able to access a interface connect to the internet or something..  I think thread solved. :)

---

### Post by The Cog on 2010-10-22
I'm fairly sure normal users can't use tcpreplay. I'm only guessing, but I think that kind of security hole would have been thought of and plugged long ago.

If you want to mark the thread solved, it's in **[COLOR="Red"]Thread Tools[/COLOR]** at the top of the page.

---

### Post by BkkBonanza on 2010-10-23
From the Tcpreplay FAQ:
> 
When tcpreplay sends packets, it injects them between the TCP/IP stack of the system and the device driver of the network card. The result is the TCP/IP stack system running tcpreplay never sees the packets.

One suggestion that has been made is using something like  VMWare,  Parallels or  Xen. Running tcpreplay in the virtual machine (guest) would allow packets to be seen by the host operating system. 

My side note:

Keep in mind that tcpreplay has no understanding of tcp protocol so cannot handle connections syn/ack exchange. It works to inject packets but cannot establish or maintain a tcp connection. It is designed for feeding a stream of packets to another system without any real local system interaction.

---

