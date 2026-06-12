---
title: "UFW Packet Filtering (bridging?)"
date: 2010-07-25
forum: Security
---

### Post by banditti on 2010-07-25
I have been using BSD's IPFW for a while.  I don't really like the way it handles FTP, among other things.  My IPFW is configured in a 3-way bridge (NIC1 to ISP feed 1, NIC 2 to ISP feed 2 and NIC 3 to internal network)  NIC1/NIC2 are in an active/passive HSRP config.

Does/Can UFW work this way?  I want to have this box be a dedicated firewall doing packet filtering without the overhead of NAT.  If I have 100 machines behind it I may want 22 open on all and 21 open on one, etc.

The UFW wiki makes sense, but it seems to be focused on protecting the machine that UFW is running on or using NAT.

Thoughts, direction?

---

### Post by bodhi.zazen on 2010-07-25
I have not heard the opinion that NAT has any significant over head before.

In general, your impression of ufw is correct, it is designed to protect the machine it is running on and less for configuration as a router.

For what you want I would suggest iptables or something more like shorewall.

---

### Post by banditti on 2010-07-25
That is what I thought, but I really dug the interface and it is so close to doing what I need.


Thanks,

---

