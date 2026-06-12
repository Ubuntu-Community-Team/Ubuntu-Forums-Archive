---
title: "Is this a bug ?"
date: 2011-12-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by matt_symes on 2011-12-01
Is this a bug ?

Connect to a wireless network that you do not store the password for. Suspend your machine. Bring your machine out of suspend but connect an Ethernet cable. 

I keep getting the wireless password window appear, every 5 minutes or so, for the wireless network i was connected to even though i am connected via Ethernet.

Can anybody else replicate this. Is it some setting i am missing ?
```

grep eth0 /var/log/syslog

<snip>
Dec  1 22:02:09 matthew-Aspire-7540 kernel: [  148.478847] tg3 0000:03:00.0: eth0: Flow control is on for TX and on for RX
Dec  1 22:02:09 matthew-Aspire-7540 kernel: [  148.479470] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec  1 22:02:09 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  1 22:02:09 matthew-Aspire-7540 NetworkManager[1125]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  1 22:02:09 matthew-Aspire-7540 dhclient: Listening on LPF/eth0/00:1f:16:c3:48:69
Dec  1 22:02:09 matthew-Aspire-7540 dhclient: Sending on   LPF/eth0/00:1f:16:c3:48:69
Dec  1 22:02:09 matthew-Aspire-7540 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec  1 22:02:09 matthew-Aspire-7540 dhclient: DHCPREQUEST of 192.168.1.105 on eth0 to 255.255.255.255 port 67
Dec  1 22:02:09 matthew-Aspire-7540 NetworkManager[1125]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec  1 22:02:09 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  1 22:02:09 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  1 22:02:09 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
<snip>

```
```

matthew@matthew-Aspire-7540:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:c3:48:69  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fec3:4869/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11270546 (11.2 MB)  TX bytes:1804200 (1.8 MB)
          Interrupt:16 
```
```

tail -n 20 /var/log/syslog

matthew@matthew-Aspire-7540:~$ tail -n20 /var/log/syslog
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Auto-activating connection 'Auto dd-wrt_vap'.
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) starting connection 'Auto dd-wrt_vap'
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0/wireless): access point 'Auto dd-wrt_vap' has security, but secrets are required.
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec  1 22:21:41 matthew-Aspire-7540 NetworkManager[1125]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <warn> No agents were available for this request.
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <warn> Activation (wlan0) failed for access point (dd-wrt_vap)
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <info> Marking connection 'Auto dd-wrt_vap' invalid.
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <warn> Activation (wlan0) failed.
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec  1 22:21:55 matthew-Aspire-7540 NetworkManager[1125]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
matthew@matthew-Aspire-7540:~$ 
```

---

