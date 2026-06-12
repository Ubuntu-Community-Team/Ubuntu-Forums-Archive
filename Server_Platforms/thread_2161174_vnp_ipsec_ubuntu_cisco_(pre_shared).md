---
title: "vnp ipsec ubuntu cisco (pre shared)"
date: 2013-07-09
forum: Server Platforms
---

### Post by optimu on 2013-07-09
I need to connect to vpn cisco from ubuntu to cisco. I must use either openswan or racoon
I tried with both, but I couldnt succeed.

with openswan, I had impression that it was working as I had this in status :


000 #33: "my_conn":4500 STATE_QUICK_I2 (sent QI2, IPsec SA established); EVENT_SA_REPLACE in 848s; newest IPSEC; eroute owner; isakmp#1; idle; import:admin initiate
000 #33: "my_conn" esp.a4855496@a.b.c.d esp.a456568@m.n.o.p tun.0@a.b.c.d tun.0@m.n.o.p ref=0 refhim=445678651
000 #34: "my_conn":4500 STATE_MAIN_I4 (ISAKMP SA established); EVENT_SA_REPLACE in 83424s; newest ISAKMP; lastdpd=-1s(seq in:0 out:0); idle; import:admin initiate

but I dont see any new interface in ifconfig

here info I received for connecting to this cisco vpn


VPN Device: Make & Model: &#8194;&#8194;&#8194;&#8194;&#8194; Cisco 3945
VPN Device: Tunnel Endpoint IP Address : a.b.c.d
Host(s):  IP address(es) to be accessed (Public IP address required) : a.b.e.f
Phase 1 & 2 Encryption Type : 3DES/SHA1

VPN Details
VPN scheme: IKE
Phase 1 encryptin algorithm: 3DES
Phase 1 hash algorithm: Secure Hash Standard
Phase 1 authentication method: Pre-Shared Key
Phase 1 algorithm: Diffie-Hellman Group 2 (1024 bit)
Phase 1 lifetime: 86400 seconds
Phase 2 perfect forward secrecy : No
Phase 2 encryption algorithm: 3DES
Phase 2 hash algorithm: Secure Hash Standard
Phase 2 lifetime: 3600 seconds


here my current ipsec.conf

config setup
        dumpdir=/var/run/pluto/

        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:25.0.0.0/8,%v6:fd00::/8,%v6:fe80::/10

        oe=off

        protostack=auto


conn my_conn

        keyingtries=0
        authby=secret
        forceencaps=yes
        auto=start
        left=m.n.o.p

        right=a.b.c.e
        rightsubnet=a.b.f.ge/32

        type=tunnel
        keylife=1h
        ikelifetime=86400s
        ike=3des-sha1;modp1024
        esp=3des-sha1

        pfs=no

does anyone see what could be the problem ?

thanks

---

