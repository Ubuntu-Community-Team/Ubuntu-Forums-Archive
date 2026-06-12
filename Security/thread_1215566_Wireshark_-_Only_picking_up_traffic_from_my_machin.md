---
title: "Wireshark - Only picking up traffic from my machine"
date: 2009-07-17
forum: Security
---

### Post by stwschool on 2009-07-17
So I've been messing about with Wireshark to teach the kids something interesting, and hopefully scare the crap out of them so that they grow up to be secure little buggers. Anyway, on my home PC and laptop, I can get traffic from other computers on the network. Promiscuous mode seems to work. At the school, no such luck. We're running a hub not a switch so that seems unlikely as a cause, I'm wondering if crappy hardware is a factor (ie LAN cards) as I didn't choose the equipment, management did and they bought cheap crap as one would expect.

Any ideas?

---

### Post by The Cog on 2009-07-17
My feeling is that the most likely explanation is that the hub is actually a switch. I think switches are so cheap these days, it wouldn't surprise me if nobody made hubs any more. But of course, I haven't seen the kit so I'm guessing.

P.S.
It occurs to me that it's so long since I used wireshark (ex ethereal) on a non-switched network, I wouldn't have noticed if wireshark had a bug and couldn't actually set promiscuous mode any more. Unlikely though.

PPS.
But I have recieved alerts from OSSEC reporting intrefaces enterning promiscuous mode when I use wireshark.

---

### Post by stwschool on 2009-07-17
I'll investigate, but it's a 40-port one and our school's rather reluctant to spend money, so I'm inclined to say they'll have got the cheapest 2nd hand junk they could find, hence my guess that it's probably a hub.

---

### Post by grayn0de on 2009-07-18
Chances are that it is a switch. I haven't seen any 40 port hubs before, but I am still pretty young. :P

In order to sniff traffic in a switched environment, you need to poison the switches arp cache. Ettercap does this extremely well. In order to do that, you need to know about your network, mainly which IP address to spoof (usually the router) and which range to poison. Effectively, you need to conduct a man-in-the-middle attack. Not too difficult, by any means, but it may set off any intrusion detection systems. Do this ONLY if you have permission and the IT department, if any, is fully aware of what you are doing (or at least management). Basic rule is to have permission before hacking the network or you can get in trouble. Trust me. ;)

Note: All information I give is for educational purposes only. I am not responsible for misuse, illegal conduct, thermo-nuclear war or swine flu.

---

### Post by InlawBiker on 2009-07-18
I would agree... I'm not young and I have never seen a 40 port hub, even when hubs were common because switches were so expensive.  The fact that you can't see anybody else's traffic tells you it's a switch.

Or perhaps your filter is set wrong.

---

### Post by stwschool on 2009-07-18
Don't worry, I have permission for this stuff, I'm not that daft! As to the filter, I tried a blank filter to see all traffic and it was only from the machine I was on. I'll have a look at the model number etc on monday and ascertain whether it's a switch or a hub.

---

### Post by Rob_H on 2009-07-18
Some switches support port mirroring that allows one port to receives all traffic for just this purpose. That might be an option. Alternatively, since you said you're only doing this for demonstration purposes, you could plug a true hub into one of the switch ports and plug a few machines into that hub so you can at least see their traffic. That should be sufficient to get your point across without compromising everyone's privacy on the switch.

---

### Post by stwschool on 2009-07-18
That sounds interesting, I'll take a look. As to the 2nd option that might be an idea, though my preference is for all the students to get to do this in a fully interactive fashion as it tends to have more impact that way. It's looking likely that I'll go down the ARP poisoning route with Ettercap (which I've got to admit looks like a really nice tool) and see where that leads me.

---

### Post by doas777 on 2009-07-18
> **grayn0de said:**
> Chances are that it is a switch. I haven't seen any 40 port hubs before, but I am still pretty young. :P

In order to sniff traffic in a switched environment, you need to poison the switches arp cache. Ettercap does this extremely well. In order to do that, you need to know about your network, mainly which IP address to spoof (usually the router) and which range to poison. Effectively, you need to conduct a man-in-the-middle attack. Not too difficult, by any means, but it may set off any intrusion detection systems. Do this ONLY if you have permission and the IT department, if any, is fully aware of what you are doing (or at least management). Basic rule is to have permission before hacking the network or you can get in trouble. Trust me. ;)

Note: All information I give is for educational purposes only. I am not responsible for misuse, illegal conduct, thermo-nuclear war or swine flu.

the reasearch I've done on it, suggests that most switches have been hardened against arp cache poisoning these days (it's a pretty old exploit), and it would degrade performance on the switch, potentially seriously. if it's a cisco switch you shoudl be able to configure a port for promiscious.

---

### Post by stwschool on 2009-07-20
Ok so it does look like I was having a dopey moment! It's a D-Link DES-1024D. I'll need to go for a more advanced approach with this by the looks of it. Thank you everyone for your help.

---

### Post by stwschool on 2009-07-20
PS I can't count, it's only 24-port!

---

### Post by doas777 on 2009-07-20
managed or unmanaged?

---

### Post by grayn0de on 2009-07-20
If it is managed, then you should be able to mirror the ports to yours (web interface?), as mentioned by [doas777]("http://ubuntuforums.org/member.php?u=451394"). As for the hardening against arp poisoning, that's true, but given that it is a D-Link and, from the sound of it, not a high-end switch that may still be an option if port mirroring is not.

One thing about port mirroring: If you only have one NIC in the machine, make sure to mirror the port with the computer on, then shut/no shut the port on the switch. If you reboot the machine with the port mirrored, you can run into problems with the monitor machine not being able to pull it's own DNS or DHCP from the server. I ran into that on my Catalyst switch and IDS box.

---

### Post by stwschool on 2009-07-20
Unmanaged, which is a pain, I could do with a nice web interface to play with :(

---

### Post by grayn0de on 2009-07-21
If it is unmanaged, try ettercap. You should be able to poison the arp cache. The thing I like most about ettercap is that it will kindly unpoison the cache when you are done.

Install ettercap:
```
sudo apt-get install ettercap
```Run it... where $IP=target_ip or range (i.e. 192.168.1.0-255)  and dump to pcap file
```
sudo ettercap -T -q -i eth0 -M arp /$IP/ -w dump.raw
```wait awhile and sniff the traffic... press 'q' when finished to stop dump and unpoison arp
read pcap file to readable packet file
```
sudo ettercap -r dump.raw >> dump.packets
```open readable file and teach the kids that someone can easily see what they are doing, if preventative measures are not in place. :D
```
sudo gedit dump.packets
```I think those commands should work, but I am not sitting at my linux box right now, so I am running from memory.

---

### Post by stwschool on 2009-07-21
Excellent, I'll give that a go once I've finished doing some maintenence on our Wine installations :)

---

### Post by wareagle on 2009-08-27
> **grayn0de said:**
> If it is unmanaged, try ettercap. You should be able to poison the arp cache. The thing I like most about ettercap is that it will kindly unpoison the cache when you are done.

Install ettercap:
```
sudo apt-get install ettercap
```Run it... where $IP=target_ip or range (i.e. 192.168.1.0-255)  and dump to pcap file
```
sudo ettercap -T -q -i eth0 -M arp /$IP/ -w dump.raw
```wait awhile and sniff the traffic... press 'q' when finished to stop dump and unpoison arp
read pcap file to readable packet file
```
sudo ettercap -r dump.raw >> dump.packets
```open readable file and teach the kids that someone can easily see what they are doing, if preventative measures are not in place. :D
```
sudo gedit dump.packets
```I think those commands should work, but I am not sitting at my linux box right now, so I am running from memory.

BTW, I've noticed in the manpage that there is an option -M arp:remote.  What is the difference between this and just -M arp?

---

