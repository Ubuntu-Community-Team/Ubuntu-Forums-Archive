---
title: "OpenVPN, can ping server and workstations but no communication with workstations"
date: 2009-04-21
forum: Server Platforms
---

### Post by awe on 2009-04-21
Hello,

Despite the countless posts that I have read, I am yet to find the way to give roadwarriors access to the whole LAN subnet at the office. They access the server well. They can ping the server's TUN0 well, they can ping the server's ETH0 and ETH1 well, and they can even ping workstations on the office subnet. However, there I have found no way for roadwarriors to communicate with the IP's in the LAN subnet (beside the server's own LAN cards), they can only ping.

This is important to me because the fax/printer at the office is connected by ethernet with a static IP. I'd like to be able to fax and print from my laptop through OpenVPN. I can ping the printer but HPLip won't find it nor configure it.

Where can I obtain some clear steps towards the solution?

LAN subnet: 192.168.10.0/24
OpenVPN subnet (TUN interfaces): 172.16.0.0/24

Communication between clients and the server itself works like a charm.

Regards, and thank you all.

---

### Post by awe on 2009-04-21
Note, for some reason now I even cannot ping workstations. It could before a reboot!

---

