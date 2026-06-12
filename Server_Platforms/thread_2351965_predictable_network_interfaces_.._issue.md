---
title: "predictable network interfaces .. issue"
date: 2017-02-08
forum: Server Platforms
---

### Post by brainiac5 on 2017-02-08
fresh install of 16.04 LTS on a HP DL360 G9. when using the standard predictable network interface names (eg: eno4 instead of eth4), the interfaces on the Intel I350 card ([COLOR=#000000][FONT=&amp]ens3f0,[/FONT][/COLOR][COLOR=#000000][FONT=&amp]ens3f1,[/FONT][/COLOR][COLOR=#000000][FONT=&amp]ens3f2,[/FONT][/COLOR][COLOR=#000000][FONT=&amp]ens3f3) [/FONT][/COLOR]do not pass traffic. i've tried unloading & reloading the igb driver, trying more updated drivers etc to no avail. however if i disable the predictable network interface naming by adding the following to /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0 biosdevname=0"

run update-grub, then reboot, the host comes back with ethX interfaces and everything works as per normal. any ideas? i would appreciate any help anyone can give as i'd like to stick with the new interface names

relevant lspci output:

```
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5719 Gigabit Ethernet PCIe (rev 01)
02:00.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5719 Gigabit Ethernet PCIe (rev 01)
02:00.2 Ethernet controller: Broadcom Corporation NetXtreme BCM5719 Gigabit Ethernet PCIe (rev 01)
02:00.3 Ethernet controller: Broadcom Corporation NetXtreme BCM5719 Gigabit Ethernet PCIe (rev 01)
04:00.0 Ethernet controller: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection (rev 01)
04:00.1 Ethernet controller: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection (rev 01)
05:00.0 Ethernet controller: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection (rev 01)
05:00.1 Ethernet controller: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection (rev 01)
82:00.0 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
82:00.1 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
82:00.2 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
82:00.3 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
```

ifconfig:
```
eno1      Link encap:Ethernet  HWaddr 94:18:82:75:2e:c8  
          inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:255.255.255.0
          inet6 addr: fe80::9618:82ff:fe75:2ec8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1062194 (1.0 MB)  TX bytes:145545 (145.5 KB)
          Interrupt:16
 
eno2      Link encap:Ethernet  HWaddr 94:18:82:75:2e:c9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17
 
eno3      Link encap:Ethernet  HWaddr 94:18:82:75:2e:ca  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16
 
eno4      Link encap:Ethernet  HWaddr 94:18:82:75:2e:cb  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17
 
eno49     Link encap:Ethernet  HWaddr 14:02:ec:89:2c:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
eno50     Link encap:Ethernet  HWaddr 14:02:ec:89:2c:a5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
ens2f0    Link encap:Ethernet  HWaddr 14:02:ec:89:a2:84  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
ens2f1    Link encap:Ethernet  HWaddr 14:02:ec:89:a2:85  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
ens3f0    Link encap:Ethernet  HWaddr 3c:a8:2a:5c:e2:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:c8300000-c83fffff
 
ens3f1    Link encap:Ethernet  HWaddr 3c:a8:2a:5c:e2:a5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:c8200000-c82fffff
 
ens3f2    Link encap:Ethernet  HWaddr 3c:a8:2a:5c:e2:a6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:c8100000-c81fffff
 
ens3f3    Link encap:Ethernet  HWaddr 3c:a8:2a:5c:e2:a7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:c8000000-c80fffff
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:25072 (25.0 KB)  TX bytes:25072 (25.0 KB)
```

dmesg:
```
[    4.908171] igb 0000:82:00.0: added PHC on eth0
[    5.076879] igb 0000:82:00.0: eth0: (PCIe:5.0Gb/s:Width x4) 3c:a8:2a:5c:e2:a4
[    5.102239] igb 0000:82:00.0: eth0: PBA No: H73100-004
[    5.211325] igb 0000:82:00.1: added PHC on eth1
[    5.211327] igb 0000:82:00.1: eth1: (PCIe:5.0Gb/s:Width x4) 3c:a8:2a:5c:e2:a5
[    5.211624] igb 0000:82:00.1: eth1: PBA No: H73100-004
[    5.279317] igb 0000:82:00.2: added PHC on eth2
[    5.279319] igb 0000:82:00.2: eth2: (PCIe:5.0Gb/s:Width x4) 3c:a8:2a:5c:e2:a6
[    5.279649] igb 0000:82:00.2: eth2: PBA No: H73100-004
[    5.348204] igb 0000:82:00.3: added PHC on eth3
[    5.348211] igb 0000:82:00.3: eth3: (PCIe:5.0Gb/s:Width x4) 3c:a8:2a:5c:e2:a7
[    5.348581] igb 0000:82:00.3: eth3: PBA No: H73100-004
[    5.404719] igb 0000:82:00.2 ens3f2: renamed from eth2
[    5.555472] igb 0000:82:00.0 ens3f0: renamed from eth0
[    5.583416] igb 0000:82:00.3 ens3f3: renamed from eth3
[    5.607571] igb 0000:82:00.1 ens3f1: renamed from eth1
[    5.608872] tg3 0000:02:00.0 eth0: Tigon3 [partno(N/A) rev 5719001] (PCI Express) MAC address 94:18:82:75:2e:c8
[    5.608929] tg3 0000:02:00.0 eth0: attached PHY is 5719C (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    5.608931] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    5.608932] tg3 0000:02:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    5.744620] tg3 0000:02:00.1 eth1: Tigon3 [partno(N/A) rev 5719001] (PCI Express) MAC address 94:18:82:75:2e:c9
[    5.760862] tg3 0000:02:00.1 eth1: attached PHY is 5719C (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    5.777180] tg3 0000:02:00.1 eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    5.793563] tg3 0000:02:00.1 eth1: dma_rwctrl[00000001] dma_mask[64-bit]
[    5.836622] tg3 0000:02:00.2 eth2: Tigon3 [partno(N/A) rev 5719001] (PCI Express) MAC address 94:18:82:75:2e:ca
[    5.853229] tg3 0000:02:00.2 eth2: attached PHY is 5719C (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    5.869934] tg3 0000:02:00.2 eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    5.888513] tg3 0000:02:00.2 eth2: dma_rwctrl[00000001] dma_mask[64-bit]
[    5.932582] tg3 0000:02:00.3 eth3: Tigon3 [partno(N/A) rev 5719001] (PCI Express) MAC address 94:18:82:75:2e:cb
[    5.949933] tg3 0000:02:00.3 eth3: attached PHY is 5719C (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    5.968523] tg3 0000:02:00.3 eth3: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    5.986776] tg3 0000:02:00.3 eth3: dma_rwctrl[00000001] dma_mask[64-bit]
[    6.004776] tg3 0000:02:00.1 eno2: renamed from eth1
[    6.039496] tg3 0000:02:00.0 eno1: renamed from eth0
[    6.067480] tg3 0000:02:00.3 eno4: renamed from eth3
[    6.127418] tg3 0000:02:00.2 eno3: renamed from eth2
[   10.494807] ixgbe 0000:04:00.1 eno50: renamed from eth1
[   10.543914] ixgbe 0000:05:00.0 ens2f0: renamed from eth2
[   10.583735] ixgbe 0000:04:00.0 eno49: renamed from eth0
[   10.619693] ixgbe 0000:05:00.1 ens2f1: renamed from eth3
```

---

### Post by howefield on 2017-02-08
Hello and welcome to the forums, please use [noparse]```

```[/noparse] tags for terminal output, it better preserves formatting aiding readability and doesn't parse text into emoticons.

---

