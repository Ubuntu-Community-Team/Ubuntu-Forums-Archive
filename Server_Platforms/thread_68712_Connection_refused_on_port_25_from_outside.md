---
title: "Connection refused on port 25 from outside"
date: 2005-09-24
forum: Server Platforms
---

### Post by yz6x on 2005-09-24
The environment:
- inet -> adsl modem (in bridge mode) -> router -> hub -> 2 PCs
1 machine is Ubuntu 5.0.4 tested with 2 kernels (2.6.10-5-686-smp and 2.6.10-5-386, it's a dual CPU machine)
2. other machine WinXP

Short version:
Port 25 closed for requests not coming from the machine's subnet.

Long version:
I've set up the Ubuntu server with apache2 and postfix.
Postfix listens on all interfaces - local loopback and eth0, both ipv4 & ipv6
Firewall is on the router with port forwarding for ports 25 and 80
to Ubuntu server.
I can send outgoing mail without problems, but it doesn't work the
other way around. Anyone trying to connect from outside gets
'port 25 connection refused' .
- Firstly I thought it was the isp blocking port 25 - checked with them and they said they don't
- I've redirected port 25 to WinXP machine and Ethereal shows incoming
SYN packet from outside to the port 25
- I've looked into the router's incoming log file and incoming smtp packet is there
- I checked Postfix for inet_interfaces etc. and it is ok
- Then I've stopped the Postfix and started Apache listening on port 25
- Again nothing ... I've then tested each and every port from 20 to 80
with apache listening on them, and I can connect to each one of them
except to the port 25.
- So it's the iptables you fool! No it's not - that was the first thing I checked
- I've tried putting the Ubuntu box in DMZ and nothing
- I've ran tethereal and tcpdump and there is nothing coming to the port 25 from the outside world (192.x.x.x network connects fine).
However (aha!), if I telnet using either external or internal ip address from the
WinXP box to port 25, then I am getting response and tcpdump clearly shows
incoming packets on port 25.
So you would say it is router or hub. Well, I tried:
- connecting the Ubuntu box directly to the router (didn't budge at all)
- changing the ip address several times

I would really appreciate any useful suggestion.

TIA...

---

### Post by yz6x on 2005-09-25
Found it:

It was Linksys WRT54G that for some reason just kept forwarding the
port 25 to the ip of my Windows box instead of to Ubuntu.
Even though I've changed ip address on my Ubuntu server and did that
as well for the port forwarding on the router (several times), the router somehow
retained the old ip address and ignored what was on its web interface.
Flashing the router with new firmware, or power cycling it was *not* enough.
I had to keep pressed reset button (on the back side of the router) for more
than 10 seconds and that did the trick.
Of course, I had to re-enter all port forwarding values as well as everything else.
Somehow I didn't trust anymore the Linksys restore utility (to get back my settings) after this experience.
I am seriously thinking of switching to HyperWRT, or DD-WRT.

I hope that this will eventually help other people save some time, if they run into the same issue.

Cheers...

---

