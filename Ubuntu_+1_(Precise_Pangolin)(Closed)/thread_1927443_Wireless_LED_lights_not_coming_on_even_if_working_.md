---
title: "Wireless LED lights not coming on even if working fine (Broadcom)"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shuttleworthwannabe on 2012-02-18
My LED lights (hardware light that shows that WiFi is on/Off is not coming on even if the drivers are installed and WiFi is working fine. Here is partial output of ```
$ sudo lshw -C network
```

Output: ```
 *-network               
       description: Wireless interface
       product: [COLOR="Red"]BCM43224[/COLOR] 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:07:f4:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-16-generic firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fbe00000-fbe03fff

```

I did not bring this up sooner--thought it would be fixed as we go along the development process in 12.04 LTS; but seems this issue has persisted at least for me since 11.04.

I have read somewhere that it could be related to "blacklisting" something --somewhere?? Can someone guide me through this process or point me in the right direction.

Thanks

---

### Post by shuttleworthwannabe on 2012-02-18
Seema like it is a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/753857").
Any takers on how to circumvent the problem before a formal fix is released?

---

### Post by cespinal on 2012-03-02
Same problem here.

---

### Post by kinggo on 2012-04-03
it's like that since 11.10

---

### Post by shuttleworthwannabe on 2012-04-05
No solution as yet I see--12.04 LTS is a beeeg milestone, this just does not look professional at all.

---

