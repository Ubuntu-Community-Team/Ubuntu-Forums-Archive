---
title: "Firewall Hits"
date: 2009-01-01
forum: Security
---

### Post by untappedpilot2 on 2009-01-01
So I'm using Xubuntu 8.10 andn I have recently started using the Firestarter GUI. I know that once you run the Firestarter wizard iptables is configured and there's no need for the GUI. However I've been using it because I occasionally need to turn the firewall off / play around with some rules / whatever. I've been noticing random incoming hits to my machine as well as outgoing ones. The outgoing connections stay in the "outgoing connections" ALL the time. I've included a screenshot of some outgoing connections as I was writing this.. The incoming hits I get will range anywhere from random udp hits off my network whether it's an ip that may or may not be assigned or the router (why would the router be pinging me?) or it's some unknown ip address with an unknown service on a 30000 + port. These outgoing hits seem to have something to do with the transmission bitTorrent client but remain open even after the program has closed. I used to be able to clear them by closing transmission and restarting x however it doesn't always work. A full restart will always do it though. What the @!@% is going on?

---

### Post by mikewhatever on 2009-01-01
You seem to have a bunch of tabs open in Firefox. Could that account for the outgoing connections? Incoming hit's is nothing uncommon. You seem to be using a router, so engage the firewall.

---

### Post by untappedpilot2 on 2009-01-01
The open tabs in Firefox are accounted for as port 80 and the service is firefox. These open ports are in the 30000+ range and are an unknown service. However, I suspect they are from transmission. What did you mean by engage the firewall? I am behind a router. I'm thinking about changing my outgoing connections to a whitelist instead of a blacklist. Are outgoing connections dangerous?

---

### Post by slowth5 on 2009-01-01
Hi untappedpilot2, 

sudo netstat -pantu 

This will provide you with all tcp and udp connections, plus the associated program, minus the sockets.

---

### Post by untappedpilot2 on 2009-01-02
I'll check that out and repost the results. However, I think I came across that command elsewhere and I believe it still showed the programs as unknown. I could be wrong though...

Also a few questions...

1. Why would my router (192.168.1.1) be listed as an UDP incoming connection (it gets blocked and shows in the event list)?

2. I also get random incoming UDP connections from my LAN.(....102, ....103..... 101) What's the deal with that? I have the only Linux box in the household and I am the only one who ever accesses files from this computer from one of the windows machines. And it happens when I'm not the one attempting to access the files.

---

### Post by The Cog on 2009-01-03
Without details, I can't tell. But most computers broadcast adverts from time to time using UDP so have a look and see if the destination is a broadcast address and also see what the port number is - this will tell you what service the packet is addressed to. Ports 137 and 138 are MS netbios for instance. My home PC sends CUPS printer announcements on port 631.

---

