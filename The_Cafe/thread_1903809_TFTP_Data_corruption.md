---
title: "TFTP Data corruption"
date: 2012-01-03
forum: The Cafe
---

### Post by Anstice on 2012-01-03
Hi guys,

I'm having some serious trouble trying to find out what happens when a tftp packet becomes corrupted between server and client. 

Is it just the case that an error code is produced or will it not be picked up on at all because the packet still arrives at the client?

N.B 
Yes it is a homework question so I'm not looking for a complete answer just confirmation as to whether I'm on the right track or not.

Thanks,
Anstice.

---

### Post by mips on 2012-01-03
> **Anstice said:**
> 
Is it just the case that an error code is produced or **will it not be picked up on at all** because the packet still arrives at the client?


tftp uses UDP (User Datagram Protocol) which does not do things like handshaking, error correction etc etc as it leaves that to higher up protocols assuming there are any in use.

[http://en.wikipedia.org/wiki/User_Datagram_Protocol](http://en.wikipedia.org/wiki/User_Datagram_Protocol)

> UDP uses a simple transmission model without implicit handshaking dialogues for providing reliability, ordering, or data integrity. Thus, UDP provides an unreliable service and datagrams may arrive out of order, appear duplicated, or go missing without notice. UDP assumes that error checking and correction is either not necessary or performed in the application, avoiding the overhead of such processing at the network interface level.

[http://en.wikipedia.org/wiki/User_Datagram_Protocol#Reliability_and_congestion_control_solutions](http://en.wikipedia.org/wiki/User_Datagram_Protocol#Reliability_and_congestion_control_solutions)

> Reliability and congestion control solutions

Lacking reliability, UDP applications must generally be willing to accept some loss, errors or duplication. Some applications such as TFTP may add rudimentary reliability mechanisms into the application layer as needed.[2]
Most often, UDP applications do not employ reliability mechanisms and may even be hindered by them. Streaming media, real-time multiplayer games and voice over IP (VoIP) are examples of applications that often use UDP. In these particular applications, loss of packets is not usually a fatal problem. If an application requires a high degree of reliability, a protocol such as the Transmission Control Protocol or erasure codes may be used instead.
Potentially more seriously, unlike TCP, UDP-based applications don't necessarily have good congestion avoidance and control mechanisms. Congestion insensitive UDP applications that consume a large fraction of available bandwidth could endanger the stability of the internet, as they frequently give a bandwidth load that is inelastic. Network-based mechanisms have been proposed to minimize potential congestion collapse effects of uncontrolled, high rate UDP traffic loads. Network-based elements such as routers using packet queuing and dropping techniques are often the only tool available to slow down excessive UDP traffic. The Datagram Congestion Control Protocol (DCCP) is being designed as a partial solution to this potential problem by adding end host TCP-friendly congestion control behavior to high-rate UDP streams such as streaming media.


Unless you perform a proper packet trace (with something like a sniffer) you would not really know what happened to the packet seeing UDP does not cater for this sort of thing.

Whenever approaching problems like this look at the underlying protocols used by the application as it's the underlying protocol that determines the behaviour.

If you want to ensure your packets do arrive implement higher level protocols or use TCP.

Hope this helps.

---

### Post by Anstice on 2012-01-03
Thanks a lot for the reply. Very helpful.

---

### Post by mips on 2012-01-03
> **Anstice said:**
> Thanks a lot for the reply. Very helpful.

You're welcome ;)

---

