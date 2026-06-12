---
title: "wifi - Could not join netdev: Operation not supported, server 18.04"
date: 2019-01-27
forum: Server Platforms
---

### Post by mauro_ita on 2019-01-27
Hi there.

I've installed an ubuntu server 18.04 with 3 NIC and a wifi card.

I managed to have these arranged as follow:
enp2s0: dhcp (for access to internet)
enp3s0, enp4s0, wlp1s0: bridge br0 (local lan)

the netplan uses networkd as renderer. This is the section about wifi:

```

  wifis:
    wlp1s0:
      optional: true
      dhcp4: no
      dhcp6: no
      access-points:
        "SSID":
          password: "SSIS_pwd"

```

this is networkctl
```

[IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  2 enp2s0           ether              routable    configured
  3 enp3s0           ether              no-carrier  configuring
  4 enp4s0           ether              no-carrier  configuring
  5 wlp1s0           wlan               off         failed
  6 br0              ether              no-carrier  configuring

```

and this is systemctl status systemd-networkd
```

&#9679; systemd-networkd.service - Network Service
   Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled-runtime; vendor preset: enabled)
   Active: active (running) since Mon 2019-01-28 01:26:08 CET; 4min 51s ago
     Docs: man:systemd-networkd.service(8)
 Main PID: 1890 (systemd-network)
   Status: "Processing requests..."
    Tasks: 1 (limit: 4642)
   CGroup: /system.slice/systemd-networkd.service
           &#9492;&#9472;1890 /lib/systemd/systemd-networkd

Jan 28 01:26:08 eye systemd-networkd[1890]: enp2s0: Link is not managed by us
Jan 28 01:26:08 eye systemd-networkd[1890]: enp4s0: Link is not managed by us
Jan 28 01:26:08 eye systemd-networkd[1890]: lo: Link is not managed by us
Jan 28 01:26:08 eye systemd-networkd[1890]: enp2s0: DHCPv4 address 10.0.0.149/24 via 10.0.0.1
Jan 28 01:26:08 eye systemd-networkd[1890]: wlp1s0: Could not join netdev: Operation not supported
Jan 28 01:26:08 eye systemd-networkd[1890]: wlp1s0: Failed
Jan 28 01:26:08 eye systemd-networkd[1890]: enp4s0: IPv6 successfully disabled
Jan 28 01:26:08 eye systemd-networkd[1890]: enp3s0: IPv6 successfully disabled
Jan 28 01:26:08 eye systemd-networkd[1890]: enp2s0: Configured
Jan 28 01:26:09 eye systemd-networkd[1890]: enp2s0: DHCPv6 address fdd1:f5cd:9b6a::a32/128 timeout preferred -1 valid -1

```

At this stage I'm confused on what to do. The chip is supported as I used the same one on a different ubuntu machine.

Any suggestion?

thanks

---

