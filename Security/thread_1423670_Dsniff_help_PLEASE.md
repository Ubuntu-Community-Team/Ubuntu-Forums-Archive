---
title: "Dsniff help PLEASE"
date: 2010-03-06
forum: Security
---

### Post by cazten on 2010-03-06
**Dsniff help PLEASE** 
Hey guys im trying to use Dsniff suite of programs for a class assignment.... Jut my luck im new to linux, and my teacher isnt even familiar with the software to help me.
 
So far i got arch linux running well, and Dsniff installed from the repositories. My problem is i cant see ANYTHING using the damn thing. So far ive just tried sticking to webspy and Dsniff. And so far ive been able to sniff Zero html pages with webspy and Zero passwords with Dsniff. 
 
Ill set it to arpspoof -t gatewayip hostip then arpspoof -t hostip gatewayip
Then enable ip forwarding via echo 1 > /proc/sys/net/ipv4/ip_forward
webspy or Dsniff will come up saying listening on eth0 (the adapter ive set it to use) but nothing ever pops up under there. It never sniffs any trafic out. 
 
also trying tcpkill i get this error
pcap_compile: syntax error
tcpkill: couldn't initialize sniffing
 
 
Can anyone PLEASE help me with this. My teacher is absolutely worthless in helping me and this project in presenting some of these utilities is worth nearly half my class grade. To get anything in this suite of programs would be acceptable, i only need to present one or two subprograms and ill be fine.
 
Im wondering if whatever is happeneing is operating system based? Something that not enabled or needs to be configured? As far as i can tell my syntax with dsniff is corect. Ive seen a couple youtubes and they are doing the same exact syntax. 
The error from tcpkill makes me think that somethings stopping me from sniffing at all?
Also with arp poisoning, without ip forwarding enabled, i should effectivley cut a computer off from the network? Even though i can get arpspoof to show info passing in both directions i dont recall any computer being cutoff even without IP forwarding. Unless thats been permanently changed somewhere in a config file to always enable.
 
 
Thanks!

---

### Post by Kinstonian on 2010-03-07
I'm pretty sure you also need to tell iptables to forward the traffic to the destination.  Anyway, for clear text protocols you could also sniff passwords without a MITM attack with ARP spoofing and forwarding by using a hub.  And for trouble shooting, you could probably also run dsniff directly on the host you're monitoring to make sure dsniff is actually working.

---

### Post by cazten on 2010-03-07
echo 1 > /proc/sys/net/ipv4/ip_forward
how do i forward in IP tables?  The one i listed above is all i know of. Ive tried dsniffing myself without any success. 

How can i sniff with arpspoofing and a hub? But eventually i really need to be able to pull this off in the classrooms switched environment. Atleast im 90% sure its switched.

---

