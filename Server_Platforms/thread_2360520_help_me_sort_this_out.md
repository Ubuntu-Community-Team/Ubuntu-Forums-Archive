---
title: "help me sort this out"
date: 2017-05-05
forum: Server Platforms
---

### Post by fishbait on 2017-05-05
my goal is to have this server share internet with minimal manual configuration, as well as act as a DNS cacheing server (bind9), cacheing proxy with antivirus(squid hopefully with squidclamav) , and file server(samba).
ubuntu 16.04 LTS
fx6300 on an asrock 990fx killer fatal1ty board
120gb toshiba-tr150 ssd as root 10gb free(rule with ssds leave free space for trim)
120gb, 850 evo(20gb swap, 90gb /tmp 10gb free)
2tb hitachi hdd (drive to share over samba)
intel quad nic and intel single nic lan (br0 starting members)
killer nic wan(enp3s0)
asus pce-n13(wireless managed by hostapd to join to br0)

>.< i tried to configure it but i now have no net on the machine itself and cant see the wireless.
someone wanna check over my ufw, hostapd, sysctl, squid, dhcpd, and bind9 configurations and tell me where ive gone wrong.
[https://filebin.ca/3LQTojJ2Un5i/etc.zip](https://filebin.ca/3LQTojJ2Un5i/etc.zip)

solved:switching to centos and starting fresh will change /tmp for /var.

---

### Post by wildmanne39 on 2017-05-05
*Thread moved to **Server Platforms**.*

---

