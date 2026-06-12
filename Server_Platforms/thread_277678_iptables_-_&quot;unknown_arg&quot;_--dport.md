---
title: "iptables - &quot;unknown arg&quot; --dport"
date: 2006-10-15
forum: Server Platforms
---

### Post by Crowhurst01 on 2006-10-15
I am getting the "unknown arg" result when i try this code:

iptables -t nat -A PREROUTING -p udp --dport 5060 -i eth0 -j DNAT --to-destination 172.16.13.197

I have researched and tried many variants, spellings and tried the full name --destination-port, for example.

I upgraded to ver. 1.3.6 of iptables and still no luck. I have even tried running known good lines from other users and still get the error

iptables v1.3.6: Unknown arg `--dport'

Optimally i would like to match an incoming packet to eth0 based on its being UDP and the port, then i want to port forward it to a destination inside the lan.

Any help is greatly appreciated.

---

### Post by fatbastard spice on 2006-10-16
Hmmm, just tried that and i couldn't get the error. The port forwarding command i'm using doesn't really look any different to yours:

iptables --table nat --append PREROUTING --protocol tcp --in-interface $OUTSIDEWORLD --dport $DCPORT -j DNAT --to $DCCLIENT:$DCPORT

I've just been using the whatever is the standard iptables version for the version of ubuntu i've got installed (which is 1.3.3 on the machine i just tested)

---

