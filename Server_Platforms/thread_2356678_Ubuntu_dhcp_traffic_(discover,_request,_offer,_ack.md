---
title: "Ubuntu dhcp traffic (discover, request, offer, ack) (i want a NACK)"
date: 2017-03-25
forum: Server Platforms
---

### Post by skillsboy on 2017-03-25
Hi I am doing a assignment and my objective is to get a NACK message from the dhcp traffic.

I already configured the class, subnet and a pool to have 2 available IP address.

To obtain the traffic message I use the command [FONT=Courier New]tcpdump -vv -i enp0s3 port 67 or 68[/FONT], then i use 3 tiny cores and use the command [FONT=Courier New]udhcpc[/FONT] on each one. 2 of then receive and Ip address and the 3rd just continues asking discover. 

So I go to ubuntu and look at the traffic and see that 2 of them  discover, request, offer and ack. And the 3rd one just keeps asking for  discover, how can I manage to see the NACK on the traffic from that  device ?

If someone knows something about this I would be very grateful.

---

