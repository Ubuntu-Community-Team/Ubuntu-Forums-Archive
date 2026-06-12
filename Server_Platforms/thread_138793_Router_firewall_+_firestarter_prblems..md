---
title: "Router firewall + firestarter prblems."
date: 2006-03-02
forum: Server Platforms
---

### Post by abadr on 2006-03-02
This seems to be more of a problem with my DSL router rather than Ubuntu/Firestarter but I would appreciate any help.

I have my Linksys WAG54g v2.0 Firmware# 1.00.19 firewall setup to only allow traffic on ports 6881, 4662, 4672 thorugh to my Ubuntu machine to use aMule and Bittorrent. Yet every once in a while Firestarter reports blocking incomming connections on ports like 55609, 51388, 53996, 47692, 34016, 42854, 54706, 55965, 56589, 59003, 59079,.... you get the idea.

Any ideas on how to prevent this from happening? Could it be that the routers firewall isn't up to par and I'm better off with a different unit?

Thanks.

---

### Post by robert_pectol on 2006-03-03
This is just a guess.  Maybe the Netfilter state module is timing out on particularly long-delayed established sessions, before your DSL router's NAT session does.  I suspect that the incoming traffic is part of an already established connection, albiet stale, for which your DSL router already has a NAT session mapped.  If the incoming traffic is truly unrelated to a previously established or ongoing session, then you've either misconfigured your router (possibly have your PC designated as the DMZ), or the router is just plain broken (buggy firmware, perhaps).  My guess is that the Netfilter state module is a little more strict regarding session timeout, which results in the blocked incoming traffic.  However, I've been known to overlook things so take that for what it's worth.  :)

---

### Post by moopere on 2006-03-03
[QUOTE=abadr]This seems to be more of a problem with my DSL router rather than Ubuntu/Firestarter but I would appreciate any help.

I have my Linksys WAG54g v2.0 Firmware# 1.00.19 firewall setup to only allow traffic on ports 6881, 4662, 4672 thorugh to my Ubuntu machine to use aMule and Bittorrent. Yet every once in a while Firestarter reports blocking incomming connections on ports like 55609, 51388, 53996, 47692, 34016, 42854, 54706, 55965, 56589, 59003, 59079,.... you get the idea.

Any ideas on how to prevent this from happening? Could it be that the routers firewall isn't up to par and I'm better off with a different unit?

Thanks.[/QUOTE]

Are you sure these blocked ports are incoming?  If they are, then you are being port scanned.  If in fact they are blocked outgoing ports then that will be amule.  I've had the same trouble here.  Although amule listens on 4662 and 4672, it spews out of every port you can imagine in the range 1-65535.  I can't find a way to stop it doing this and had to open the whole machines outgoing port range in order to make amule work.

Cheers,
Craig

---

### Post by robert_pectol on 2006-03-05
[QUOTE=moopere]Are you sure these blocked ports are incoming?  If they are, then you are being port scanned.[/QUOTE]
Unless his DSL router is configured to have his PC designated as the DMZ host, those types of packets shouldn't ever arrive at his box to be picked up by his firewall.

[QUOTE=moopere]If in fact they are blocked outgoing ports then that will be amule.  I've had the same trouble here.  Although amule listens on 4662 and 4672, it spews out of every port you can imagine in the range 1-65535.  I can't find a way to stop it doing this and had to open the whole machines outgoing port range in order to make amule work.[/QUOTE]
Doesn't Firestarter simply configure the firewall to allow all outbound connections to any port, by default?  I realize it can probably be configured to restrict outgoing traffic to conform to a more strict policy/ruleset.  Just curious about Firestarter's default behavior regarding outbound traffic.  I've never played with Firestarter but I know Iptables well enough.  Anyway, hopefully he figures it out and let's us know.  It does seem curious.

---

### Post by abadr on 2006-03-07
Thanks for all your replies. 

I have no DMZ configured .

I tried to see if the problem is the Netfilter state timing out before NAT by checking to see if any of the connected aMule client's IP matches that of the blocked attacks/scans as reported by the firewall. This was really tough as aMule doesn't have an easy way to list the IP of the clients in the ever changing queue. It dawned on me to check my windows machine on the LAN which has no services running that listens to the outside world except Skype. The Zone Alarm firewall log showed that this machine experiences the same attacks/scans. So I guess that would rule out this possibility.

I also updated the firmware to version 1.01.15 but that didn't fix the problem. it seems there are less attacks/scans but I'm not sure. 

Yes FireStarter by default allows all outgoing traffic and it can configured to deny all outgoing traffic and white lists only selected ports. 

Since I found this out I freaked out and turned off all services shared from the Linux box that serves my LAN and as you can imagine that really hampered my style, so I need to figure this out.

Any idea?

I'm thinking of buying maybe another cheap DSL (D-Link perhaps) and test its firewall. Anything else I can try before doing that?

Thanks.

---

