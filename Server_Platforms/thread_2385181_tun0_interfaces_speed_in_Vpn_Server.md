---
title: "tun0 interfaces speed in Vpn Server"
date: 2018-02-17
forum: Server Platforms
---

### Post by secoonder on 2018-02-17
[COLOR=#000000][FONT=&amp]Hello [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]i am using Ubuntu 14.04 Firewall+VPN Server.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]35 Client connect to My vpn Server.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]i want to increase tun0 speed.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]My tun0 speed configuration is ;
[/FONT][/COLOR]> root@xxxxx:~# ethtool tun0
Settings for tun0:
        Supported ports: [ ]
        Supported link modes:   Not reported
        Supported pause frame use: No
        Supports auto-negotiation: No
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        MDI-X: Unknown
        Current message level: 0xffffffa1 (-95)
                               drv ifup tx_err tx_queued intr tx_done rx_status pktdata hw wol 0xffff8000
        Link detected: yes
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
tun0 was seems 10 Mb/s.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]i wrote below code,but it wasnt

[/FONT][/COLOR]> [COLOR=#000000]ethtool -s eth0 speed 1000 duplex full[/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]How can i increase tun0 speed in Linux?[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]Thank you very much for your help[/FONT][/COLOR]

---

### Post by TheFu on 2018-02-17
Are you certain that the reported speed is really a cap?  I'm not seeing that here.  The link speed is just a placeholder according to openvpn docs.  [https://community.openvpn.net/openvpn/ticket/347](https://community.openvpn.net/openvpn/ticket/347)

---

### Post by wildmanne39 on 2018-02-17
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

