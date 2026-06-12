---
title: "Monitoring my LAN web traffic - how?"
date: 2010-05-24
forum: Server Platforms
---

### Post by garfonzo on 2010-05-24
Hey there,

I have a number of computers on a LAN. There are 3 laptops and 1 desktop, all running windows. I also have a Ubuntu server in the garage which servers up files to all those on the LAN. The server is not visible outside of the LAN for security reasons. 

Now, I want to track all traffic from any computer in my house that is coming and going in and out from the inter-tubes. I do not want to add this as a service to my current server as (a) it is behind the LAN and (b) I don't want to mess with security issues with that server. 

I think I could set up a computer (an extra) which is between the modem and the router with two ethernet cards which would be able to monitor all traffic coming and going. This computer would, obviously, be exposed to all potential attacks as it wouldn't be behind the router's firewall. I'm not sure exactly how that would like or what software to use. 

Anyone have any suggestions? 

P.S. The only other person in the house is my wife and I discussed the idea of tracking all web surfing habits with her. She is in full support of setting up this type of thing.

---

### Post by terazen on 2010-05-24
Bind and OpenDNS can track dns requests if that's what you're looking for.  You'd just need some sort of dyndns for OpenDNS.

I also use BandwidthD that is built into a pfSense box, but it only shows ip addresses and ports.  I'm not familiar with anything that lists url, ip, and port.

---

### Post by ArchCast on 2010-05-24
Perhaps iptraf may be something that might work for you?

```

 apt-get install iptraf
```

---

