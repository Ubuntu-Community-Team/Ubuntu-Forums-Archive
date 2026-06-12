---
title: "Wireless security"
date: 2009-11-24
forum: Security
---

### Post by Pasdar on 2009-11-24
Is it possible to check all traffic of anyone using your wifi router? If that would be possible, then it would also be possible to write a program to filter anything you're interested in and save that? No? (assuming the data was not encrypted)

How would one go about doing that? Sniff all traffic going in and out from the router?

---

### Post by madnessjack on 2009-11-24
Depending on the make of your router you can check for people logged in via a web interface. If you type the gateway address into your browser (something like 10.0.0.2, again, depending on your router and how it's been set up) you can usually log-in to it.

What router are you using?

---

### Post by ice60 on 2009-11-24
it's called a man-in-the-middle attack and has to be done locally. there are loads of videos and tutorials. here's one
[http://www.youtube.com/watch?v=ciuv5n5cmzs](http://www.youtube.com/watch?v=ciuv5n5cmzs)

i haven't seen the video i want to watch the news, it's coming on now!

[http://www.youtube.com/results?search_query=ettercap+arp+poisoning&search_type=&aq=1&oq=Ettercap+](http://www.youtube.com/results?search_query=ettercap+arp+poisoning&search_type=&aq=1&oq=Ettercap+)

---

### Post by jflaker on 2009-11-24
since this is your network, you can put an inline proxy (goes between your router and your isp connection.

From there, you have access to all packets in and out of your network, but nothing ON your network....

Hijacking a connection would be more difficult than this forum allows for...an inline host is the easiest...

---

### Post by Grenage on 2009-11-24
> **Pasdar said:**
> Is it possible to check all traffic of anyone using your wifi router? If that would be possible, then it would also be possible to write a program to filter anything you're interested in and save that? No? (assuming the data was not encrypted)

How would one go about doing that? Sniff all traffic going in and out from the router?

Yes, a basic packet sniffer will do what you need; assuming you are authenticated and on the network...and your card supports promiscuous mode.

---

### Post by Xbehave on 2009-11-24
1) Your router may support it
2) You can put a devices between your router and your modem to sniff everything
2b)You can do a MITM attack on your router to get all data sent to your PC (I've never done a MITM so it may be tricky)
3) You can attack the wireless part of the protocol
if your next to the router you will pick-up almost everything, but if your setup is something like A----B-R-C----D/Y, then you might pick up data from BCD but not A (you will see all data to anybody though, so this isn't really an issue) but should be kept in mind while filtering.
I think, the best way to get the data is to use aircrack
If the connection is encrypted you will need to use airdecap-ng to decrypt the data before filtering
If there is more than one router in range, you should filter data collected with airodump-ng to avoid wasting lots of disc space.

Once you have the data (from a sniffer/MITM attack/aircrack) you can filter it using tools for pcap files or browse it using wireshark.

---

### Post by Pasdar on 2009-11-24
All the following is theoretical (just talking about interesting things):

I guess on a home network it would be doable since there is 'minimal' traffic. Of course if you have to go through the packets manually you'd go crazy, but it is automatable.

How about a network with thousands of users, thousands of wireless access points and even more wired access points. The traffic must be insane really, and if we look at it at the 'packet level' its even crazier.

I imagine all this information first goes to a router, probably several, most likely a super computer. Now I'm wondering about two things:

1. As an administrator of this network, how much processing power do you guys think would be needed to analyze everything sent and received from this network? Is it doable? Maybe having a supercomputer to go through everything real time and save things of interest.

2. As a user of this network I don't think its possible. Since there is just way too much traffic going on and pulling all this information to your PC would be too much to handle by your connection/your PC and your program would simply crash. The admin would probably also notice the B/W usage at your location. However theoretically:
 2a. if all this information is being sent to a supercomputer somewhere, whereabouts unknown.. IP could probably be found. Assuming we're assigned an IP, and so we're part of the network at user-level only. Would it be possible to scan all traffic (real time) and and filter for interesting things?

What if you get many computers on the same network to do the same for a set range of IPs, store interesting things separately, and those PCs again send to a central location?

I guess what i'm wondering about just how much access one has to all on-going traffic as a user on a modern-well-secured network. I guess only an admin of such a network or someone who has tested would know the answer. :)

---

### Post by __p1n__ on 2009-11-24
Trivial.  Put the access point in its own vlan and put a deep-packet inspection appliance (commercial or roll-your-own) between it and the router.

---

### Post by Grenage on 2009-11-26
Why the hell would you need to bother with a separate VLAN?

---

