---
title: "vsftpd - sizing the hardware for a C100K"
date: 2016-03-29
forum: Server Platforms
---

### Post by J_Arunkumar on 2016-03-29
Team,

Looking to size the hardware for FTP (vsftpd) for handling 50k - 100k concurrent FTP connections.  

Any experience, guidelines, configuration that you could share would be highly appreciated.

TIA

---

### Post by TheFu on 2016-03-29
Welcome to the forums.  That's a big question. Need lots more data to answer.

* Can you use a more friendly-to-firewalls protocol, like HTTP?
* Concurrent connections is just 1 part of the question.
* How much data will be transferred?
* How large is the WAN pipe?
* How large is the LAN pipe?
* How small is the network to all the devices?
* Is the FTP connection passive or active?

Basically, you need to calculate total bandwidth, time-to-download, for each client connection.

I once had to deploy tftp to support up to 30M devices.  Then we looked at the problem a little more and determined that 30M wasn't ever gonna happen, but 2M might after a huge power outage.  The payloads were relatively small - 4MB, so we took the lowest downstream bandwidth numbers and used those for each client-device.  I was only involved with the infrastructure sizing, design, network design and purchases, not directly with the deployment, so I don't know the exact tuning performed. Sorry.  

Hope this makes sense.

---

