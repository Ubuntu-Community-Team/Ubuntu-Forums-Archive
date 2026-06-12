---
title: "Does IPSEC work with IPV6?"
date: 2010-07-18
forum: Security
---

### Post by movieman on 2010-07-18
While I'm on the subject of IPSEC, does anyone have IPSEC working with IPV6 using racoon? 

I have two systems which are talking to each other with IPSEC on IPV4 and can talk to each other without IPSEC on IPV6. I configured them to also use IPSEC on IPV6, but when I try to ping6 one machine from the other, nothing happens; syslog shows that racoon has decided it needs to negotiate a connection, but it never sends an ISAKMP message to the other machine, so it just times out. The logs even say that it's going to send the message to the correct IPV6 address, it just never does:

Jul 18 02:28:58 nightmare racoon: DEBUG: 100 bytes from xxxx[500] to xxxx[500]
Jul 18 02:28:58 nightmare racoon: DEBUG: sockname xxxx[500]
Jul 18 02:28:58 nightmare racoon: DEBUG: send packet from xxxx[500]
Jul 18 02:28:58 nightmare racoon: DEBUG: send packet to xxxx[500]
Jul 18 02:28:58 nightmare racoon: DEBUG: src6 xxxx[500] 0
Jul 18 02:28:58 nightmare racoon: DEBUG: dst6 xxxx[500] 0
Jul 18 02:28:58 nightmare racoon: DEBUG: 1 times of 100 bytes message will be sent to xxxx[500]
Jul 18 02:28:58 nightmare racoon: DEBUG: resend phase1 packet 53b231fc25ce2252:0000000000000000
Jul 18 02:29:08 nightmare racoon: ERROR: phase1 negotiation failed due to time up. 53b231fc25ce2252:0000000000000000

Wireshark shows nothing actually coming out of eth0.

I've found a couple of IPSEC/IPV6/racoon tutorials on the web, but doing exactly what they say to do just doesn't work.

---

### Post by wacky_sung on 2010-07-18
I think you have double posting it.If your ISP does not support you with IPv6 and no way you can run it on IPv6.Otherwise the answer is yes.

[http://www.ipv6verify.com/](http://www.ipv6verify.com/)

---

### Post by movieman on 2010-07-18
No, IPV6 works, IPSEC works on IPV4, but IPSEC doesn't work on IPV6 even though the debug output shows that it's detected an IPSEC configuration and is intending to send a message to negotiate a connection... the message just disappears between the debug output and the network interface.

Incidentally I disabled the firewalls on both machines and it still didn't send a negotiation message out, so that's not the problem. Interestingly I can see occasional ISAKMP messages coming from one machine checking whether there's a connection ('dead peer detection' or whatever they're called), but I can't see any trying to negotiate such a connection.

---

