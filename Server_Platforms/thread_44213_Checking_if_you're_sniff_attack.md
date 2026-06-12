---
title: "Checking if you're sniff attack"
date: 2005-06-24
forum: Server Platforms
---

### Post by ron126 on 2005-06-24
Can the command 'traceroute' shows you whether you are being sniff attack?

---

### Post by ubuntu_demon on 2005-06-25
[QUOTE=ron126]Can the command 'traceroute' shows you whether you are being sniff attack?[/QUOTE]
 no
You should try the package snort if you want to do that.

---

### Post by jdong on 2005-06-25
what do you mean? man-in-the-middle attacks? Packet logging/capture?

---

### Post by LordHunter317 on 2005-06-25
You can't tell if someone is sniffing you trivally, even inside your own network borders.  Within your network borders, there are some ways to tell if someone is trying to sniff all the network traffic, but it requires network hardware that's smarter than the stuff you would have in a house.

Outside your network borders, you must assume it is being sniffed, even if it isn't.

---

### Post by ron126 on 2005-06-25
> You should try the package snort if you want to do that

Yeah, snort can do the job. and i think the unix command "ifconfig -a" can help you find if there's a sniffer in your network. Just type "ifconfig -a" in terminal and look for "PROMISC". Im still not quite sure about this anyway, will find out more with google.

> 
what do you mean? man-in-the-middle attacks? Packet logging/capture?

i mean Man in the middle attack (ARP POISON), sorry by the way, my networking knowledge is still quite misleading, 

> Outside your network borders, you must assume it is being sniffed, even if it isn't.

That's really S*ck , hehe

---

### Post by jdong on 2005-06-26
[QUOTE=ron126]Yeah, snort can do the job. and i think the unix command "ifconfig -a" can help you find if there's a sniffer in your network. Just type "ifconfig -a" in terminal and look for "PROMISC". Im still not quite sure about this anyway, will find out more with google.
[/quote]
No, you can't. PROMISC only tells you that YOU have a sniffer running on YOUR system. It doesn't say anything about another computer being a sniffer on your network or another system intercepting your requests.


> 
i mean Man in the middle attack (ARP POISON), sorry by the way, my networking knowledge is still quite misleading, 

No prob. that's a bit clearer now. Traceroute can ONLY help you in a MITM attack if you know what the full path to the destination host is. In other words, it's a pretty weak bet (Hop # 24 to google.com changed... new ISP router or sniffer? ;) )

The best way of avoiding a MITM attack is using an encrypted protocol, like HTTPS or SSH, for important communications.

---

### Post by LordHunter317 on 2005-06-26
[QUOTE=ron126]i mean Man in the middle attack (ARP POISON), sorry by the way, my networking knowledge is still quite misleading, [/quote]Look for an ARP posioning attack requires nothing more than tcpdump, a promiscious interface, and some patience.  It also requires knowing all the MAC address of every NIC on your network, and what IP address they should have.

Why are you worried?  Usually under ARP poisioing, machines will stop responding.  And in the enterprise, proper network hardware makes them very difficult or impossible to pull off without being detected, assuming it's properly setup and all that.

---

### Post by ron126 on 2005-06-27
> No, you can't. PROMISC only tells you that YOU have a sniffer running on YOUR system. It doesn't say anything about another computer being a sniffer on your network or another system intercepting your requests

i see, thanks


> Why are you worried?  Usually under ARP poisioing, machines will stop responding.  And in the enterprise, proper network hardware makes them very difficult or impossible to pull off without being detected, assuming it's properly setup and all that.


I just want to know if there's is a way to find out if someone on the same LAN as me  
has Arp poison the network, i wouldn't want my password to be stolen (nobody wants).  Excluding using the excrypted protocol like SSL or HTTPS (because some websites doesn't support), is snort the only solution? Any other security tools to help you determined the arp poisoning activity in LAN?


>  Usually under ARP poisioing, machines will stop responding

Really?

---

### Post by LordHunter317 on 2005-06-27
[QUOTE=ron126]I just want to know if there's is a way to find out if someone on the same LAN as me  
has Arp poison the network,[/quote]There is, but like I said, it's difficult to reliably determine.  You have to know the assignment of every IP address and what MAC address should have it to make this determination.  It's a PITA.

I'm not sure ARP poision attacks are even very common, as there is usually eaiser and faster ways to get what you want.

> i wouldn't want my password to be stolen (nobody wants).Then when you have to send it over the network, only transmit it over protocols that provide authenticity and encryption, like SSL and SSH.  

> Excluding using the excrypted protocol like SSL or HTTPS (because some websites doesn't support), is snort the only solution?The better solution would be to use a different password for these websites.

> Any other security tools to help you determined the arp poisoning activity in LAN?TCPdump to monitor the network and that list of addresses and MACs, like I said.  If someone is trying to posion, you'll see arp traffic where one NIC claims to have an IP address it shouldn't.

If there is an IP collision, it should be reported.  Linux will log to the kernel, and Windows will pop up a message.  When that happens, you know something suspect is going on.




Really?[/QUOTE]

---

