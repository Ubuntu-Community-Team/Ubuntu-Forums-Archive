---
title: "Firewall issue via VPN"
date: 2011-05-04
forum: Security
---

### Post by rmarc71 on 2011-05-04
I have a OpenWRT device connecting via OpenVPN to my server at home.  The VPN works fine.

I'm having an issue with the outbound connection to the Internet
via the VPN after a few minutes.

When I connect initially, it's fine; after a few minutes new connections stop processing from the VPN (existing connections, say largish downloads, continue until complete).  If I restart the firewall, it will work again for a few minutes then stop again.  I see the traffic coming in from the VPN interface, but it just seems to get dropped silently after those first initially good few minutes (nothing in the FW logs about it at all).  I can get to the local services on ${MYIP} from VPN clients without issue, it's only the outbound connections that stop.

I'm using Firehol with the following interface and router configurations (br0 is my internet interface, br1 is my VPN interface):
-----------------------------------------------------------------
interface br0 InetLocal src "${MYNET}" dst "${MYIP}"
        policy drop
        server "${PUBLIC_SERVICES}" accept
        client all accept

interface br1 VPN src "${VPNNET}"
        policy drop
        client all accept

interface br0 InboundInet src not "${UNROUTABLE_IPS}" dst "${MYIP}"
        protection strong
        policy drop

        if [ ! -z "${TRUSTED_PCS}" -a ! -z "${TRUSTED_SERVICES}" ]
        then
                server "${TRUSTED_SERVICES}" accept src "${TRUSTED_PCS}"
        fi

        server "${PUBLIC_SERVICES}" accept
        client all accept

router InternetRouter inface br0 outface br0 src "${MYNET}" dst not "${UNROUTABLE_IPS} ${MYNET}"

router VPN2Inet inface br1 outface br0
        masquerade
        route all accept
-----------------------------------------------------------------
Linux myhost 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

iptables -V
iptables v1.4.10

I just upgraded to (server) 11.04, but had the same issues on 10.10.

---

