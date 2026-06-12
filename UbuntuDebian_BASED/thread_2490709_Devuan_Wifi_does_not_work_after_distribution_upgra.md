---
title: "Devuan: Wifi does not work after distribution upgrade to Daedalus."
date: 2023-09-13
forum: Ubuntu/Debian BASED
---

### Post by maketopsite on 2023-09-13
Could it please be caused by Microcode SW error ?


```
/var/log/syslog


2023-09-12T17:17:38.455883+02:00 maketopsite NetworkManager[2009]: <info>  [1694531858.4558] device (wlan0): supplicant interface state: disconnected -> authenticating
2023-09-12T17:17:38.456361+02:00 maketopsite kernel: [  227.202914] wlan0: send auth to xxxxxxxx (try 1/3)
2023-09-12T17:17:38.456377+02:00 maketopsite kernel: [  227.203034] iwlwifi 0000:05:00.0: Microcode SW error detected.  Restarting 0x2000000.
2023-09-12T17:17:38.456379+02:00 maketopsite kernel: [  227.203049] iwlwifi 0000:05:00.0: Loaded firmware version: 18.168.6.1 135-6.ucode
2023-09-12T17:17:38.456383+02:00 maketopsite kernel: [  227.203182] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
2023-09-12T17:17:38.456384+02:00 maketopsite kernel: [  227.203184] iwlwifi 0000:05:00.0: Status: 0x0000004C, count: 6
2023-09-12T17:17:38.456385+02:00 maketopsite kernel: [  227.203186] iwlwifi 0000:05:00.0: 0x000014E1 | ADVANCED_SYSASSERT
2023-09-12T17:17:38.456386+02:00 maketopsite kernel: [  227.203187] iwlwifi 0000:05:00.0: 0x00019DA8 | uPc
2023-09-12T17:17:38.456388+02:00 maketopsite kernel: [  227.203189] iwlwifi 0000:05:00.0: 0x00019E0E | branchlink1
2023-09-12T17:17:38.456389+02:00 maketopsite kernel: [  227.203190] iwlwifi 0000:05:00.0: 0x00019E0E | branchlink2
2023-09-12T17:17:38.456390+02:00 maketopsite kernel: [  227.203191] iwlwifi 0000:05:00.0: 0x0000EB3A | interruptlink1
2023-09-12T17:17:38.456391+02:00 maketopsite kernel: [  227.203193] iwlwifi 0000:05:00.0: 0x00000000 | interruptlink2
2023-09-12T17:17:38.456392+02:00 maketopsite kernel: [  227.203194] iwlwifi 0000:05:00.0: 0x00000000 | data1
2023-09-12T17:17:38.456394+02:00 maketopsite kernel: [  227.203195] iwlwifi 0000:05:00.0: 0x00000000 | data2
2023-09-12T17:17:38.456396+02:00 maketopsite kernel: [  227.203197] iwlwifi 0000:05:00.0: 0x000000A2 | line
2023-09-12T17:17:38.456397+02:00 maketopsite kernel: [  227.203198] iwlwifi 0000:05:00.0: 0x00018C6E | beacon time
2023-09-12T17:17:38.456398+02:00 maketopsite kernel: [  227.203199] iwlwifi 0000:05:00.0: 0x00000392 | tsf low
2023-09-12T17:17:38.456399+02:00 maketopsite kernel: [  227.203201] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
2023-09-12T17:17:38.456401+02:00 maketopsite kernel: [  227.203202] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
2023-09-12T17:17:38.456402+02:00 maketopsite kernel: [  227.203203] iwlwifi 0000:05:00.0: 0x00014952 | time gp2
2023-09-12T17:17:38.456403+02:00 maketopsite kernel: [  227.203204] iwlwifi 0000:05:00.0: 0x00000000 | time gp3
2023-09-12T17:17:38.456405+02:00 maketopsite kernel: [  227.203206] iwlwifi 0000:05:00.0: 0x754312A8 | uCode version
2023-09-12T17:17:38.456406+02:00 maketopsite kernel: [  227.203207] iwlwifi 0000:05:00.0: 0x00000120 | hw version
2023-09-12T17:17:38.456407+02:00 maketopsite kernel: [  227.203208] iwlwifi 0000:05:00.0: 0x00C80300 | board version
2023-09-12T17:17:38.456408+02:00 maketopsite kernel: [  227.203210] iwlwifi 0000:05:00.0: 0x0000001C | hcmd
2023-09-12T17:17:38.456410+02:00 maketopsite kernel: [  227.203211] iwlwifi 0000:05:00.0: 0x00022008 | isr0
2023-09-12T17:17:38.456411+02:00 maketopsite kernel: [  227.203212] iwlwifi 0000:05:00.0: 0x00000000 | isr1
2023-09-12T17:17:38.456412+02:00 maketopsite kernel: [  227.203213] iwlwifi 0000:05:00.0: 0x00000602 | isr2
2023-09-12T17:17:38.456414+02:00 maketopsite kernel: [  227.203215] iwlwifi 0000:05:00.0: 0x0141FCC0 | isr3
2023-09-12T17:17:38.456415+02:00 maketopsite kernel: [  227.203216] iwlwifi 0000:05:00.0: 0x00000000 | isr4
2023-09-12T17:17:38.456416+02:00 maketopsite kernel: [  227.203217] iwlwifi 0000:05:00.0: 0x00010110 | isr_pref
2023-09-12T17:17:38.456417+02:00 maketopsite kernel: [  227.203218] iwlwifi 0000:05:00.0: 0x000291D2 | wait_event
2023-09-12T17:17:38.456419+02:00 maketopsite kernel: [  227.203220] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
2023-09-12T17:17:38.456420+02:00 maketopsite kernel: [  227.203221] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
2023-09-12T17:17:38.456440+02:00 maketopsite kernel: [  227.203222] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
2023-09-12T17:17:38.456442+02:00 maketopsite kernel: [  227.203224] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
```


```
[ 5436.647225] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5489.971095] wlan0: deauthenticating from xxxxxxxx by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5490.185219] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5490.283595] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5516.937758] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5517.036260] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5517.705690] wlan0: authenticate with xxxxxxxx
[ 5517.708287] wlan0: send auth to xxxxxxxx (try 1/3)
[ 5517.710245] wlan0: authenticated
[ 5517.710681] wlan0: waiting for beacon from xxxxxxxx
[ 5517.720607] wlan0: associate with xxxxxxxx (try 1/3)
[ 5517.724182] wlan0: RX AssocResp from xxxxxxxx (capab=0x411 status=0 aid=3)
[ 5517.728379] wlan0: associated
[ 5518.773211] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5750.381685] wlan0: deauthenticating from xxxxxxxx by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5750.569842] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5750.665822] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5755.869950] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5755.965822] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[ 5756.055582] wlan0: authenticate with xxxxxxxx
[ 5756.065564] wlan0: send auth to xxxxxxxx (try 1/3)
[ 5756.083132] wlan0: authenticated
[ 5756.083537] wlan0: waiting for beacon from xxxxxxxx
[ 5756.110381] wlan0: associate with xxxxxxxx (try 1/3)
[ 5756.114058] wlan0: RX AssocResp from xxxxxxxx (capab=0x411 status=0 aid=3)
[ 5756.119130] wlan0: associated
[ 5756.198564] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```


```
# ip l
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether xxxxxxx2 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether xxxxxxx3 brd ff:ff:ff:ff:ff:ff
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether xxxxxxx4 brd ff:ff:ff:ff:ff:ff
5: br-xxxxxxx8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether xxxxxxx5 brd ff:ff:ff:ff:ff:ff
```


```
# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether xxxxxxx2 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether xxxxxxx3 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.33/24 brd 10.0.0.255 scope global dynamic wlan0
       valid_lft 86219sec preferred_lft 86219sec
    inet6 xxxxxxx6/64 scope global dynamic noprefixroute 
       valid_lft 86387sec preferred_lft 3587sec
    inet6 xxxxxxx7/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether xxxxxxx4 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
5: br-xxxxxxx8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether xxxxxxx5 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-xxxxxxx8
       valid_lft forever preferred_lft forever
```


```
# nmcli d
DEVICE           TYPE      STATE                  CONNECTION      
wlan0            wifi      connected               w....        
lo               loopback  connected (external)  lo              
br-xxxxxxx8      bridge    connected (external)  br-xxxxxxx8 
docker0          bridge    connected (external)  docker0         
eth0             ethernet  unavailable   
```


```
# lspci -v
05:00.0 Network controller: Intel Corporation Centrino Wireless-N 135 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 135 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```


```
# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by maketopsite on 2023-09-17
Ethernet connection to internet does not work either.

---

### Post by maketopsite on 2023-11-06
It works after few reboots, I don't know what causes that.

---

