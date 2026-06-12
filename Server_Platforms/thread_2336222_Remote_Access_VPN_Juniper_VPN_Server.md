---
title: "Remote Access VPN Juniper VPN Server"
date: 2016-09-06
forum: Server Platforms
---

### Post by Eloge_Bapfunya on 2016-09-06
I am trying to setup a remote access VPN from my Ubuntu server 14.04 to a Juniper router acting as a VPN Server.
The Juniper has this settings:
- Authentication method: PSK
- Encryption Schema: ike
- Perfect Forward Secrecy- IKE
- Encryption Algorithm 3DES
- Hashing Algorithm SHA
- Renegotiate IKE SA every 86400 Sec
- IPSec ESP
- Perfect Forward Secrecy-IPSEC Group 2
- Encryption Algorithm IPSec 3DES
- Hashing Algorithm IPSec SHA
- Renegotiate IPSec SA every 3600 Sec

I setup openswang and configure my ipsec like this:

```
conn leo
        authby=secret
        keyingtries=3
        rekey=yes
        keylife=1h
        type=tunnel
        keyexchange=ike
        ike=3des-md5-modp1024,aes256-sha1-modp1024
        ikelifetime=86400s
        phase2=esp
        phase2alg=3des-md5;modp1024


        pfs=yes
        left=10.10.0.113       


        right=x.y.z.n        
        rightsubnet= *.*.*.*

        auto=add
```


When I launch ipsec verification, I got:

```
xyz@Radius:/home/ubadmin# ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.38/K3.13.0-24-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [OK]
        [FAILED]


  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!


        [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [FAILED]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [WARNING]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]



```


Thank you to help me to figure out what is going wrong with this configuration.

---

