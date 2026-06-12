---
title: "Server keeps dropping Intenret Connection"
date: 2010-08-23
forum: Server Platforms
---

### Post by tronic_ on 2010-08-23
hi, 

i mentioned a strange behaviour at my server 10.04. i can connect to all local network clients, but can't get out into the internet. sometimes it works, sometimes it doesn't. seems the server can't find the dns servers, but i use the same for the client computers (these are the isp nameservers).

another strange thing is, when i start my calendarserver, the internet stops working as well!

after a reboot it works again, but after some time or by starting calendar server it drops again!

any advice?

regards

---

### Post by Thijs Koetsier on 2010-08-23
Random dropping of the internet connection only happens to me when I have two (or more) machines using the same IP-addresses.

If you're not using a network where local addresses are distributed by DHCP, but static addresses are used, then check whether or not another device connected to the network isn't using the same IP address.

Should that not solve it, try changing the network adapter.

---

### Post by snek on 2010-08-23
Any chance you are not using a router but a hub/switch between your modem & computers? If so the last one to request an IP will be the only one with internet access..

---

### Post by Thijs Koetsier on 2010-08-23
> **snek said:**
> Any chance you are not using a router but a hub/switch between your modem & computers? If so the last one to request an IP will be the only one with internet access..

If you use a switch that won't happen and neither with a HUB; those devices are made to share internet connections.

The only difference is that a Switch knows where to send which packet, and a HUB just sends it out globally so all clients can get it. That might slow your network down, but still leaves the system of sharing the connection intact.

---

