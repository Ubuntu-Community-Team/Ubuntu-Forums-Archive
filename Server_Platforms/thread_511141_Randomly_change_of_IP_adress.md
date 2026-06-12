---
title: "Randomly change of IP adress"
date: 2007-07-27
forum: Server Platforms
---

### Post by Jimmyfj on 2007-07-27
Hi folks

I have a Feisty server running on my AMD Athlon 64 with onboard LAN. Lately I have seen some strange behavior from the server which is randomly changing its own IP address. 

The server is connected to a Linksys router which redirects incoming traffic from my static IP address at my ISP. After a day of rest to save electricity the server sometimes have changed its IP address when it's up and running therefore I have to re-enter the IP in my routers forwarding table. Is this normal behavior ? I've never seen 6.10 Edgy 32 bit server do this. What can I do to avoid those random changes in server IP address?

---

### Post by Subnet on 2007-07-27
From your post I'm guessing that you have the server setup for dhcp, is this correct? Have you tried setting it with a static IP address?

---

### Post by Modernity on 2007-07-27
That would be a good start, setting a static IP on your server. Try that first then if it still changes, we can go from there.

---

### Post by Jimmyfj on 2007-07-27
Thank you very much - I've set it to static IP and will be testing it over the next few days. I'll report back if it continues. 

Jimmy

---

