---
title: "Need Help, Advice and Information in setting up a server"
date: 2009-01-03
forum: Server Platforms
---

### Post by StephenD on 2009-01-03
I am very new to Linux, but do have some experience with Windows Networking.  Though I have recently run into a couple of issues with our network.

Our existing network is based around an Active Directory Windows Server 2003 box that acts as the domain controller, primary DNS, DHCP server, VPN server and file server.

We recently got a new network scanner with a feature that sends a scan to a network directory, but it will not send it to an Active Directory network so I planned to get a cheap computer and stick Ubuntu on it and set the share on that computer.  I do not anticipate a significant need for a great deal of security on this server as the only things it will host initially will be scans which should not remain in their directory long.  I am assuming that this will be straight forward and easy, please let me know if I am mistaken.

I was also recently told to look into setting up video conferencing on almost no budget.  I am looking at using netmeeting as it is free and I believe that everyone who will need to access it has XP.  The problem I ran into here is that I no longer have a running 2000 server and do not have the budget for two junk servers so I was wondering if anyone knows of an ILS server that will run on Ubuntu.

---

### Post by mbeach on 2009-01-03
is this the sort of thing you are looking for?

[http://www.tldp.org/HOWTO/NetMeeting-HOWTO/netmeetserver.html](http://www.tldp.org/HOWTO/NetMeeting-HOWTO/netmeetserver.html)

I've never tried it as I don't use netmeeting but it looks credible enough and the links are active.

edit:
a search for:
[http://www.google.com/search?q=linux+ILS+server](http://www.google.com/search?q=linux+ILS+server)
yields server howto's so, I'd guess that it is quite possible to run your ILS service on a Linux machine.

---

