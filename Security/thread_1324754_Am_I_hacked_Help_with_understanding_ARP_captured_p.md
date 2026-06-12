---
title: "Am I hacked? Help with understanding ARP captured packages..."
date: 2009-11-12
forum: Security
---

### Post by Limeni on 2009-11-12
Noob here, Im new to linux, I play around with Wireless hot spots. 

Now this is what my problem is, when I connect to wireless network, and monitor traffic with wireshark i get tons of ARP packages, they look like this:
 
7    0.007114    GigasetC_8f:92:a9    Broadcast    ARP    Who has 192.168.5.9?  Tell 192.168.5.1

and the IP adress, 192.168.5.9 is increasing by one every time, so i get 200, 300 of these with different IP adress, every time its increesed by one. 

Is that mean someone on the network is trying to attack me? Is that ARP poisoning? Or is that normal? It looks to me like someone is trying all the IP adresses, Im noob, I dont know, but it looks strange to me...

Im new to linux, player around with BT3 for 2,3 months, and now Im on single boot Ubuntu. I love Linux, and i would like to learn as much as i can about wireless security so I hope you will help me with my noob questions [IMG]http://forums.remote-exploit.org/images/smilies/smile.gif[/IMG]

So is so many ARP packages normal? It looks like i posted up, but IP is increasing by one every time.

---

### Post by SteveHillier on 2009-11-12
I have not seen this in Wireshark myself.
I assume 192.168.5.1 is your router.  Is this then the router polling to determine who is on the network?
How frequently are these ARP messages occurring?
Are you able in Wireshark to turn off some of the messages leaving only the ones you are looking for?

---

### Post by Limeni on 2009-11-12
Im connected to a hotspot, 192.168.5.1 is router Im connected to.

I get like 1ARP package in every secund. 

It looks like he is trying all IP adresses and trying to tell 192.168.5.1 who is on every IP adress.

 Is this then the router polling to determine who is on the network? -> I really don know, I dont even know what is router polling, i dont even know what is ARP, I read some turorials about ARP sniffing and the man in the middle and thats it. I do understand principales but I dont know how to use attack or protect my self from it. 

One more question, does iptables protect me from ARP sniffing?

---

### Post by SteveHillier on 2009-11-13
I have just run wireshark on my Windows machine and yes there are ARP requests every .3 seconds or so.

Use the following link to get an idea on ARP
[http://www.tildefrugal.net/tech/arp.php](http://www.tildefrugal.net/tech/arp.php)

If you did use iptables to block ARP messages I suspect your machine might just stop working.  I suspect it would denied the right to see the rest of your network.

You can filter out ARP messages from your wireshark trace if you want to reduce the amount of messages you are looking at.

---

### Post by skbhat03 on 2009-11-13
Make sure you have configured your IP tables correctly as stated above.
In case you do not know to configur ur IP tables, you can use Firestarter. Which is GUI based and easy to configure IP tables.
Once configured correctly, others will find it difficult to getinto your system.

---

### Post by koenn on 2009-11-13
it's normal ARP behaviour : ARP tries to map ip addresses to mac addresses, because ethernet needs MAC addresses in order to work. 

The fact that you see the entire ip range being queried may mean that someone is trying to connect to each address in the range, which might mean somene is scanning the network. This could be a legit network monitoring program, or a malicious scan. There's no way of knowing. It could also just mean that there are a lot of hosts on the network and some servers (dns, proxy, ...) need to talk to them.

---

### Post by __p1n__ on 2009-11-13
> **SteveHillier said:**
> If you did use iptables to block ARP messages I suspect your machine might just stop working.  I suspect it would denied the right to see the rest of your network.

Qft although it's not a case of deny but rather just-wouldn't-work.

---

