---
title: "network not connected after reboot"
date: 2020-04-23
forum: Server Platforms
---

### Post by michael_ger on 2020-04-23
I installed Ubuntu server 20.04 beta when it was released and switched on and ran "apt update / apt upgrade" every day.
For about a week now, the network is not connected when I start the computer. 
I had to connect a monitor and keyboard to log in and run "dhclient enp2s0". Then the computer gets his ipv4 address and I can connect via ssh.  

I never had to configure that the dhcp client should run. It always did work out of the box. Why not now? What did change in the last week?
How can I permanently switch on the dhcp client?
Do I have to use now this "netplan" as the ubuntu server documentation is suggesting? [https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)  

```
root@fileserver:~# uname -a Linux fileserver 5.4.0-26-generic #30-Ubuntu SMP Mon Apr 20 16:58:30 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

PS: enp2s0 has a 1GBit/s Ethernet connection to a simple 192.168.0.x home network.

---

### Post by slickymaster on 2020-04-23
*Thread moved to **Server Platforms**.*

---

### Post by michael_ger on 2020-04-23
I checked my boot logs from 20th April where DHCP still worked and from today.
I only copied (AFAIK) network related messages:

DHCP working booting Ubuntu 20.04
```

journalctl -b-11
---------
Apr 20 22:16:08 fileserver kernel: Linux version 5.4.0-25-generic (buildd@lcy01-amd64-014) (gcc version 9.3.0 (Ubuntu 9.3.0-10ubuntu>
...
Apr 20 22:16:08 fileserver kernel: libphy: r8169: probed
Apr 20 22:16:08 fileserver kernel: r8169 0000:03:00.0 eth0: RTL8168c/8111c, 00:e0:4d:8a:b1:b7, XID 3c4, IRQ 29
Apr 20 22:16:08 fileserver kernel: r8169 0000:03:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
...
Apr 20 22:16:08 fileserver kernel: r8169 0000:03:00.0 enp3s0: renamed from eth0
...
Apr 20 22:16:08 fileserver systemd[1]: Set hostname to <fileserver>.
...
Apr 20 22:16:08 fileserver systemd[1]: Starting Network Service...
...
Apr 20 22:16:08 fileserver systemd[1]: Started Network Service.
Apr 20 22:16:08 fileserver systemd[1]: Starting Wait for Network to be Configured...
Apr 20 22:16:08 fileserver kernel: RTL8211B Gigabit Ethernet r8169-300:00: attached PHY driver [RTL8211B Gigabit Ethernet] (mii_bus:>
Apr 20 22:16:08 fileserver kernel: r8169 0000:03:00.0 enp3s0: Link is Down
...
Apr 20 22:16:08 fileserver systemd-sysctl[443]: Not setting net/ipv4/conf/all/promote_secondaries (explicit setting exists).
Apr 20 22:16:08 fileserver systemd-sysctl[443]: Not setting net/ipv4/conf/default/promote_secondaries (explicit setting exists).
Apr 20 22:16:08 fileserver systemd-networkd[451]: Enumeration completed
Apr 20 22:16:08 fileserver systemd-networkd[451]: enp3s0: IPv6 successfully enabled
Apr 20 22:16:08 fileserver systemd-networkd[451]: enp3s0: Link UP
...
Apr 20 22:16:08 fileserver systemd-udevd[461]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
...
Apr 20 22:16:09 fileserver systemd[1]: Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
Apr 20 22:16:09 fileserver systemd-udevd[464]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
...
Apr 20 22:16:10 fileserver systemd-networkd[451]: enp3s0: Gained carrier
Apr 20 22:16:10 fileserver kernel: .
Apr 20 22:16:10 fileserver kernel: r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
Apr 20 22:16:10 fileserver kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
Apr 20 22:16:10 fileserver systemd-networkd[451]: enp3s0: DHCPv4 address 192.168.0.103/24 via 192.168.0.1
...
Apr 20 22:16:11 fileserver systemd-networkd[451]: enp3s0: Gained IPv6LL
Apr 20 22:16:11 fileserver systemd-networkd-wait-online[471]: managing: enp3s0
Apr 20 22:16:11 fileserver systemd[1]: Finished Wait for Network to be Configured.
...

```

...and today. No DHCP and no configured network interface - why?
```

journalctl -b
-------
Apr 23 14:56:55 fileserver kernel: Linux version 5.4.0-26-generic (buildd@lcy01-amd64-029) (gcc version 9.3.0 (Ubuntu 9.3.0-10ubuntu>
...
Apr 23 14:56:55 fileserver kernel: libphy: r8169: probed
Apr 23 14:56:55 fileserver kernel: r8169 0000:02:00.0 eth0: RTL8168c/8111c, 00:e0:4d:8a:b1:b7, XID 3c4, IRQ 25
Apr 23 14:56:55 fileserver kernel: r8169 0000:02:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
Apr 23 14:56:55 fileserver kernel: r8169 0000:02:00.0 enp2s0: renamed from eth0
...
Apr 23 14:56:55 fileserver systemd-sysctl[408]: Not setting net/ipv4/conf/all/promote_secondaries (explicit setting exists).
Apr 23 14:56:55 fileserver systemd-sysctl[408]: Not setting net/ipv4/conf/default/promote_secondaries (explicit setting exists).
...
Apr 23 14:56:56 fileserver systemd-udevd[420]: Using default interface naming scheme 'v245'.
Apr 23 14:56:56 fileserver systemd-udevd[420]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
Apr 23 14:56:56 fileserver systemd-networkd[434]: Enumeration completed
Apr 23 14:56:56 fileserver systemd[1]: Started Network Service.
Apr 23 14:56:56 fileserver systemd[1]: Starting Wait for Network to be Configured...
Apr 23 14:56:56 fileserver systemd[1]: Finished Wait for Network to be Configured.
...
Apr 23 14:56:56 fileserver systemd[1]: Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
Apr 23 14:56:56 fileserver systemd-udevd[433]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
...
Apr 23 14:57:01 fileserver systemd[1]: Starting Network Name Resolution...
Apr 23 14:57:01 fileserver systemd[1]: Starting Network Time Synchronization...
...
Apr 23 14:57:01 fileserver systemd[1]: Reached target Network.
Apr 23 14:57:01 fileserver systemd[1]: Reached target Network is Online.
Apr 23 14:57:01 fileserver systemd[1]: Reached target Host and Network Name Lookups.
...
Apr 23 14:57:02 fileserver sshd[1093]: Server listening on 0.0.0.0 port 22.
Apr 23 14:57:02 fileserver networkd-dispatcher[1043]: No valid path found for iwconfig
Apr 23 14:57:02 fileserver systemd[1]: Started OpenBSD Secure Shell server.
...
Apr 23 14:57:25 fileserver snapd[1056]: autorefresh.go:385: Cannot prepare auto-refresh change due to a permanent network error: per>
Apr 23 14:57:48 fileserver snapd[1056]: stateengine.go:150: state ensure error: persistent network error: Get https://api.snapcraft.>
Apr 23 14:58:32 fileserver systemd[1]: nmbd.service: start operation timed out. Terminating.
Apr 23 14:58:32 fileserver systemd[1]: nmbd.service: Failed with result 'timeout'.
Apr 23 14:58:32 fileserver systemd[1]: Failed to start Samba NMB Daemon.
...
Apr 23 15:22:25 fileserver snapd[1056]: autorefresh.go:385: Cannot prepare auto-refresh change due to a permanent network error: per>
Apr 23 15:22:25 fileserver snapd[1056]: stateengine.go:150: state ensure error: persistent network error: Get https://api.snapcraft.>
Apr 23 15:42:25 fileserver snapd[1056]: autorefresh.go:385: Cannot prepare auto-refresh change due to a permanent network error: per>
Apr 23 15:42:25 fileserver snapd[1056]: stateengine.go:150: state ensure error: persistent network error: Get https://api.snapcraft.>
...

```

After local login and running ```
dhclient enp2s0
```
```

...
Apr 23 15:48:31 fileserver kernel: RTL8211B Gigabit Ethernet r8169-200:00: attached PHY driver [RTL8211B Gigabit Ethernet] (mii_bus:>
Apr 23 15:48:31 fileserver systemd-networkd[434]: enp2s0: Link UP
Apr 23 15:48:31 fileserver kernel: r8169 0000:02:00.0 enp2s0: Link is Down
Apr 23 15:48:31 fileserver dhclient[1497]: DHCPREQUEST for 192.168.0.103 on enp2s0 to 255.255.255.255 port 67 (xid=0x433e39d7)
Apr 23 15:48:33 fileserver systemd-networkd[434]: enp2s0: Gained carrier
Apr 23 15:48:33 fileserver kernel: r8169 0000:02:00.0 enp2s0: Link is Up - 1Gbps/Full - flow control rx/tx
Apr 23 15:48:34 fileserver dhclient[1497]: DHCPREQUEST for 192.168.0.103 on enp2s0 to 255.255.255.255 port 67 (xid=0x433e39d7)
Apr 23 15:48:34 fileserver dhclient[1497]: DHCPACK of 192.168.0.103 from 192.168.0.1 (xid=0xd7393e43)
Apr 23 15:48:34 fileserver systemd[1]: Reloading Samba SMB Daemon.
Apr 23 15:48:34 fileserver systemd[1]: Reloaded Samba SMB Daemon.
Apr 23 15:48:34 fileserver systemd-timesyncd[1010]: Network configuration changed, trying to establish connection.
Apr 23 15:48:34 fileserver systemd[1]: Stopping Network Name Resolution...
Apr 23 15:48:34 fileserver systemd[1]: systemd-resolved.service: Succeeded.
Apr 23 15:48:34 fileserver systemd[1]: Stopped Network Name Resolution.
Apr 23 15:48:34 fileserver systemd[1]: Starting Network Name Resolution...
Apr 23 15:48:35 fileserver systemd-resolved[1536]: Positive Trust Anchors:
Apr 23 15:48:35 fileserver systemd-resolved[1536]: . IN DS 20326 8 2 e06d44b80b8f1d39a95c0b0d7c65d08458e880409bbc683457104237c7f8ec8d
Apr 23 15:48:35 fileserver systemd-resolved[1536]: Negative trust anchors: 10.in-addr.arpa 16.172.in-addr.arpa 17.172.in-addr.arpa 1>
Apr 23 15:48:35 fileserver systemd-resolved[1536]: Using system hostname 'fileserver'.
Apr 23 15:48:35 fileserver systemd[1]: Started Network Name Resolution.
Apr 23 15:48:35 fileserver dhclient[1497]: bound to 192.168.0.103 -- renewal in 16464 seconds.
...

```

---

### Post by michael_ger on 2020-04-24
After some sleep and another inspection of the boot logs...
The difference seems to be the PHY driver for the Realtek network. In the boot log of the 20th of April where DHCP was working the "kernel: PHY attached" comes directly after "kernel: r8169..." messages.
With the current kernel there is no such message in the whole boot up sequence.

from todays bootlog (no DHCP during boot up):
```

Apr 24 09:02:59 fileserver kernel: r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Apr 24 09:02:59 fileserver kernel: libphy: r8169: probed
Apr 24 09:02:59 fileserver kernel: r8169 0000:02:00.0 eth0: RTL8168c/8111c, 00:e0:4d:8a:b1:b7, XID 3c4, IRQ 25
Apr 24 09:02:59 fileserver kernel: r8169 0000:02:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
Apr 24 09:02:59 fileserver kernel: r8169 0000:02:00.0 enp2s0: renamed from eth0

```

only after I locally log in and run "dhclient enp2s0"

```

Apr 24 09:06:27 fileserver kernel: RTL8211B Gigabit Ethernet r8169-200:00: attached PHY driver [RTL8211B Gigabit Ethernet] (mii_bus:>
Apr 24 09:06:28 fileserver systemd-networkd[443]: enp2s0: Link UP
Apr 24 09:06:28 fileserver kernel: r8169 0000:02:00.0 enp2s0: Link is Down
Apr 24 09:06:28 fileserver dhclient[1504]: DHCPDISCOVER on enp2s0 to 255.255.255.255 port 67 interval 3 (xid=0xf0b4ed2b)
Apr 24 09:06:29 fileserver systemd-networkd[443]: enp2s0: Gained carrier
Apr 24 09:06:29 fileserver kernel: r8169 0000:02:00.0 enp2s0: Link is Up - 1Gbps/Full - flow control rx/tx
Apr 24 09:06:29 fileserver kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
Apr 24 09:06:31 fileserver dhclient[1504]: DHCPDISCOVER on enp2s0 to 255.255.255.255 port 67 interval 4 (xid=0xf0b4ed2b)
Apr 24 09:06:31 fileserver dhclient[1504]: DHCPOFFER of 192.168.0.103 from 192.168.0.1
Apr 24 09:06:31 fileserver dhclient[1504]: DHCPREQUEST for 192.168.0.103 on enp2s0 to 255.255.255.255 port 67 (xid=0x2bedb4f0)
Apr 24 09:06:31 fileserver dhclient[1504]: DHCPACK of 192.168.0.103 from 192.168.0.1 (xid=0xf0b4ed2b)
Apr 24 09:06:31 fileserver systemd-networkd[443]: enp2s0: Gained IPv6LL
...

```

---

### Post by michael_ger on 2020-04-24
It seems the bug is reported and fixed for others: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1871182](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1871182)

unfortunately, not for my hardware. There seem to be different PHYs with different drivers...

---

### Post by kalle12 on 2020-04-24
The bug you refer to was about something different, read the description carefully. You even have a different network chip type, RTL8168c instead of RTL810xE.
The "attached PHY driver" message is displayed when opening the net_device. Means your network isn't brought up by whatever network manager.

---

### Post by michael_ger on 2020-04-24
Thank you for your comment.
How can I figure out which network manager is managing my network?

I just installed the server version of Ubuntu 20.04 and did daily update/upgrade. I tried Samba and ZFS but did not change/configure network devices.
It did work for the first days as expected (automatically got an ipv4 address via DHCP).

---

### Post by michael_ger on 2020-04-24
I found a config file:
/etc/netplan/00-installer-config.yaml

The content was:
```

# This is the network config written by 'subiquity'
network:
  ethernets:
    enp3s0:
      dhcp4: true
  version: 2

```

But, my network interface is enp2s0.
After changing enp3s0 to enp2s0 my Ubuntu boots up as expected with an active network interface with an ip address it got via DHCP.

I have no idea why my network interface name seems to have changed (I only removed an USB3 PCIe adapter a few days ago).
And it seems for Ubuntu server 20.04 the network is configured by netplan (never heard of this before) as mentioned in the documentation: [https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)

The problem is solved for me.

---

### Post by mwhudson2 on 2020-04-27
> **michael_ger said:**
> I found a config file:
/etc/netplan/00-installer-config.yaml

The content was:
```

# This is the network config written by 'subiquity'
network:
  ethernets:
    enp3s0:
      dhcp4: true
  version: 2

```

But, my network interface is enp2s0.
After changing enp3s0 to enp2s0 my Ubuntu boots up as expected with an active network interface with an ip address it got via DHCP.

I have no idea why my network interface name seems to have changed (I only removed an USB3 PCIe adapter a few days ago).


Huh, that's definitely not supposed to happen! You can see the different nic names in the boot logs you posted though (enp3s0: renamed from eth0 / [COLOR=#000000][FONT=&amp]enp2s0: renamed from eth0). Can you look through your logs to see when it happened? I guess it happening when you added / removed hardware seems most likely but that would still be a bug.[/FONT][/COLOR]

---

