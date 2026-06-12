---
title: "iptables to redirect traffic back to its source"
date: 2011-05-03
forum: Security
---

### Post by Gakumerasara on 2011-05-03
I'm currently using a homemade Python script to parse script kiddie IP addresses from logfiles.  To this point, I've simply been DROPping any requests from these IPs using iptables.  I thought it might be fun to redirect their traffic back to them, but as I am not an expert at iptables, I was wondering if I should use FORWARD or PREROUTING.  Thanks for the information.

---

### Post by Gakumerasara on 2011-05-03
bump, bump, bump, get bump, now let's go...  house.

---

### Post by The Cog on 2011-05-04
I like that idea. I think you will have to use the PREROUTING rule because you have to use the mangle command which I think only applies to PREROUTING and POSTROUTING chains. But I'm not at all sure that it will have much effect - it will not be able to complete a connection unless the 3-way handshake completes, and to do that you would have to also change the source address to be yourself so that the replies get back to you. So in effect you need to swap the source and destination IP addresses.

---

### Post by unspawn on 2011-05-04
> **Gakumerasara said:**
> I thought it might be fun to redirect their traffic back to them
Note remote hosts may well include anything from proxies to compromised systems running automated tasks so chances anyone noticing it, or it having any effect except ISPs seeing odd ingress traffic, is about zilch.

---

### Post by Dave_L on 2011-05-04
Is it possible that the source IP was spoofed, so that the traffic would be bounced to the wrong place?

---

### Post by deconstrained on 2011-05-04
Simply using the reject chain as opposed to the drop chain would put less strain on the TCP/IP stack than return-to-sender, because instead of having to send copies of the packets back, the firewall just has to send a "rejected" message packet.

Furthermore, from what I've read, reject is a generally good policy; if drop is used all the time, clients will continually send packets trying to connect, because they'll be assuming in that case that it's a network issue that's causing packet dropping, and that will also increase the load.

---

### Post by Agent ME on 2011-05-05
Sending traffic back just makes denial of service attempts twice as effective against you.

---

### Post by Gakumerasara on 2011-05-06
Thanks for the feedback!

Just a couple of quick comments...  This isn't intended to address DoS attacks; it's intended for people scanning for security loopholes.  At best, I'm hoping it will cause the villains to attempt to break into their own computers or perhaps their proxy/ies (wasted effort and/or **** off their proxy service).

I guess I'm more lost than I thought I was when it comes to iptables.  Please let me know if this is on the right track.  (I will hopefully be able to test it later today.)```

iptables -t mangle -A PREROUTING -s <villain_ip> --to-destination <villain_ip>
iptables -t mangle -A POSTROUTING -s $WAN_IP -d <villain_ip> -j SNAT --to <villain_ip>
iptables -A FORWARD -d <villain_ip> -j ACCEPT

```

---

