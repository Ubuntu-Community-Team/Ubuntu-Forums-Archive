---
title: "Multiple responses to an IP"
date: 2010-05-05
forum: Server Platforms
---

### Post by JoshS on 2010-05-05
I have been banging my head about this problem for a while now and I can't seem to come up with a solution.

I have an Ubuntu 8.04 LTS server running with about 100 users. The server is running DHCP and I'm having a problem with more than one user responding to an IP address. The users are spread out over a pretty significant distance and probably have 5 switches between them. The odd part to me is that the two users will both respond if I try to connect to x.x.x.211 but one of them will also respond to x.x.x.92. If I telnet into the .92 box by using the .211 address and check the ip settings, it tells me it's ip is .92. 

I'm still pretty new to Linux in general so I've been searching all over for similar problems, but haven't found anything that seems to match up.

---

### Post by terazen on 2010-05-05
Does this happen when any computer pings the .211 address or just 1?  If it's just 1 it could be the arp table on the pc.

What does `arp -n` say after pinging .92 and .211?

---

### Post by uberlinuxnerd on 2010-05-05
This is almost certainly ARP. Are any of the switches managed?

---

### Post by JoshS on 2010-05-05
The switches are managed. 

after pinging both from the server, and running arp -n, .211 and .92 are both showing the same mac address. 

I've been suspecting ARP as a problem as somewhere else I found to run arping on the address and I get mixed results between the two MAC's

---

### Post by terazen on 2010-05-05
Does this happen from every pc that tries to ping the .92 and .211 or just the 1?

---

### Post by JoshS on 2010-05-05
I don't know if it matters, but the only connections I have to the network are an ssh session with the server, and then I am VPN'd into the network as well from my win7 box. From my machine and through the server I'm getting the same results.

---

### Post by psusi on 2010-05-05
What does sudo ifconfig say on the machine with both addresses?  It must have been configured to listen on both.

---

### Post by JoshS on 2010-05-05
The boxes receiving addresses are actually radio modems. They have a pretty limited list of commands I can run on them. As far as networking I can basically just set them to Static/DHCP and get the settings of the connection.

---

### Post by uberlinuxnerd on 2010-05-06
Clear the ARP table on the managed switches and the problem should clear... you may need to get the boxes to request their IP again.

---

### Post by psusi on 2010-05-06
It isn't an ARP table issue.  The machines populate their ARP table by broadcasting asking "who is using this IP?"  And they only cache it for a limited time.  If a machine has the wrong mapping in its ARP table then it will send the packet to the wrong address, and the receiver will simply ignore it, not respond.

If the machine is responding to that IP address then it is because it is configured to listen on that address.

---

