---
title: "Openvpn no internet connection Ubuntu 15.10 client"
date: 2016-02-18
forum: Security
---

### Post by m1gu3l on 2016-02-18
[COLOR=#000000]Hello, [/COLOR]
[COLOR=#000000]Have been looking for threads on my issue, but have so far not been able to solve my problem. After upgrading to ubuntu 15.10, I can connect using openvpn and I am able to access resources on the network but cannot reach the internet. Strange thing is that on some wifi networks it does work while other hotspots it doesn't.[/COLOR]

[COLOR=#000000]I do not believe it is a problem with the server since using windows to connect works without a problem. Even using openvpn on a windows 8.1 vm on my ubuntu 15.10 works flawlessly, however on ubuntu 15.10 nothing. [/COLOR]

[COLOR=#000000]I have tried with both openvpn from command line and openvpn-network-manager, both methods give me the same result.[/COLOR]

[COLOR=#000000]Any help would be much appreciated.

Syslog during connection below:
[/COLOR]```
Feb 18 21:37:05 user-ThinkPad-X230 NetworkManager[826]: <info>  Starting VPN service 'openvpn'...
Feb 18 21:37:05 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 14999
Feb 18 21:37:05 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN service 'openvpn' appeared; activating connections
Feb 18 21:37:05 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN plugin state changed: starting (3)
Feb 18 21:37:05 user-ThinkPad-X230 NetworkManager[826]: nm-openvpn-Message: openvpn started with pid 15005
Feb 18 21:37:05 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN connection 'pfsense-udp-1194-routed-user' (ConnectInteractive) reply received.
Feb 18 21:37:05 user-ThinkPad-X230 nm-openvpn[15005]: OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jan  4 2016
Feb 18 21:37:05 user-ThinkPad-X230 nm-openvpn[15005]: library versions: OpenSSL 1.0.2d 9 Jul 2015, LZO 2.08
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: WARNING: file '/home/user/Documents/pfsense-udp-1194-user-routed/pfsense-udp-1194-user.p12' is group or others accessible
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: WARNING: file '/home/user/Documents/pfsense-udp-1194-user-routed/pfsense-udp-1194-user-tls.key' is group or others accessible
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: Control Channel Authentication: using '/home/user/Documents/pfsense-udp-1194-user-routed/pfsense-udp-1194-user-tls.key' as a OpenVPN static key file
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: UDPv4 link local: [undef]
Feb 18 21:37:06 user-ThinkPad-X230 nm-openvpn[15005]: UDPv4 link remote: [AF_INET]148.250.13.121:1194
Feb 18 21:37:09 user-ThinkPad-X230 nm-openvpn[15005]: [openvpn-server] Peer Connection Initiated with [AF_INET]148.250.13.121:1194
Feb 18 21:37:11 user-ThinkPad-X230 nm-openvpn[15005]: TUN/TAP device tap0 opened
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWLINK: name:tap0 index:18 flags:0x00001002
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: RTM_NEWLINK: name:tap0 index:18 flags:0x00001002
Feb 18 21:37:11 user-ThinkPad-X230 nm-openvpn[15005]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --tap -- tap0 1500 1590 10.0.0.21 255.255.255.0 init
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): new Tun device (carrier: OFF, driver: 'tun', ifindex: 18)
Feb 18 21:37:11 user-ThinkPad-X230 systemd-udevd[15010]: Could not generate persistent MAC address for tap0: No such file or directory
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN connection 'pfsense-udp-1194-routed-user' (IP Config Get) reply received.
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN connection 'pfsense-udp-1194-routed-user' (IP4 Config Get) reply received.
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN Gateway: 148.250.13.121
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  Tunnel Device: tap0
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  IPv4 configuration:
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Internal Gateway: 10.0.0.1
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Internal Address: 10.0.0.21
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Internal Prefix: 24
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Internal Point-to-Point Address: 0.0.0.0
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Maximum Segment Size (MSS): 0
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Static Route: 10.0.0.0/24   Next Hop: 10.0.0.1
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Static Route: 10.0.1.0/24   Next Hop: 10.0.0.1
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    Forbid Default Route: no
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>    DNS Domain: '(none)'
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  No IPv6 configuration
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN plugin state changed: started (4)
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWLINK: name:tap0 index:18 flags:0x00011043
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: RTM_NEWLINK: name:tap0 index:18 flags:0x00011043
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: Adding interface tap0 index:18
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWADDR: index:18, addr:10.0.0.21
Feb 18 21:37:11 user-ThinkPad-X230 avahi-daemon[803]: Joining mDNS multicast group on interface tap0.IPv4 with address 10.0.0.21.
Feb 18 21:37:11 user-ThinkPad-X230 avahi-daemon[803]: New relevant interface tap0.IPv4 for mDNS.
Feb 18 21:37:11 user-ThinkPad-X230 avahi-daemon[803]: Registering new address record for 10.0.0.21 on tap0.IPv4.
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWADDR: index:3, addr:10.0.2.170
Feb 18 21:37:11 user-ThinkPad-X230 nm-openvpn[15005]: Initialization Sequence Completed
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  VPN connection 'pfsense-udp-1194-routed-user' (IP Config Get) complete.
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): link connected
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWROUTE: index:18
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: RTM_NEWROUTE: index:18
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  NetworkManager state is now CONNECTED_LOCAL
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  keyfile: add connection in-memory (9c39aa5c-8758-4499-b260-582acb2c20e7,"tap0")
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.586580] bridge-wlp3s0: disabling the bridge
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  Device 'tap0' has no connection; scheduling activate_check in 0 seconds.
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): Activation: starting connection 'tap0' (9c39aa5c-8758-4499-b260-582acb2c20e7)
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWLINK: name:tap0 index:18 flags:0x00011043
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWADDR: index:18, addr:10.0.0.21
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_NEWROUTE: index:18
Feb 18 21:37:11 user-ThinkPad-X230 dbus[806]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb 18 21:37:11 user-ThinkPad-X230 vmnet-natd: RTM_DELROUTE: index:18
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  NetworkManager state is now CONNECTED_LOCAL
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  Policy set 'tap0' (tap0) as default for IPv4 routing and DNS.
Feb 18 21:37:11 user-ThinkPad-X230 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  Writing DNS information to /sbin/resolvconf
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: Stopped bridge wlp3s0 to virtual network 0.
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: Started bridge tap0 to virtual network 0.
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: RTM_NEWLINK: name:tap0 index:18 flags:0x00011043
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: RTM_NEWROUTE: index:18
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: RTM_DELROUTE: index:18
Feb 18 21:37:11 user-ThinkPad-X230 dnsmasq[961]: setting upstream servers from DBus
Feb 18 21:37:11 user-ThinkPad-X230 dnsmasq[961]: using nameserver 8.8.8.8#53
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616863] bridge-wlp3s0: down
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616872] bridge-wlp3s0: detached
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616910] /dev/vmnet: open called by PID 1356 (vmnet-bridge)
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616919] /dev/vmnet: hub 0 does not exist, allocating memory.
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616937] /dev/vmnet: port on hub 0 successfully opened
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616947] bridge-tap0: up
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616953] bridge-tap0: attached
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.616993] bridge-tap0: disabling the bridge
Feb 18 21:37:11 user-ThinkPad-X230 dbus[806]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 18 21:37:11 user-ThinkPad-X230 NetworkManager[826]: <info>  (tap0): Activation: successful, device activated.
Feb 18 21:37:11 user-ThinkPad-X230 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 18 21:37:11 user-ThinkPad-X230 nm-dispatcher: Dispatching action 'vpn-up' for tap0
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: Stopped bridge tap0 to virtual network 0.
Feb 18 21:37:11 user-ThinkPad-X230 vmnetBridge: Started bridge wlp3s0 to virtual network 0.
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648850] bridge-tap0: down
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648857] bridge-tap0: detached
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648893] /dev/vmnet: open called by PID 1356 (vmnet-bridge)
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648901] /dev/vmnet: hub 0 does not exist, allocating memory.
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648917] /dev/vmnet: port on hub 0 successfully opened
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648925] bridge-wlp3s0: device is wireless, enabling SMAC
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648927] bridge-wlp3s0: up
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.648932] bridge-wlp3s0: attached
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.776712] userif-3: sent link down event.
Feb 18 21:37:11 user-ThinkPad-X230 kernel: [ 7377.776714] userif-3: sent link up event.
Feb 18 21:37:13 user-ThinkPad-X230 avahi-daemon[803]: Joining mDNS multicast group on interface tap0.IPv6 with address fe80::447f:5eff:fe8e:c884.
Feb 18 21:37:13 user-ThinkPad-X230 avahi-daemon[803]: New relevant interface tap0.IPv6 for mDNS.
Feb 18 21:37:13 user-ThinkPad-X230 avahi-daemon[803]: Registering new address record for fe80::447f:5eff:fe8e:c884 on tap0.*.
Feb 18 21:37:21 user-ThinkPad-X230 nm-dispatcher: Dispatching action 'up' for tap0
Feb 18 21:37:31 user-ThinkPad-X230 whoopsie[821]: [21:37:31] Cannot reach: https://daisy.ubuntu.com
Feb 18 21:37:31 user-ThinkPad-X230 whoopsie[821]: [21:37:31] offline
Feb 18 21:37:31 user-ThinkPad-X230 whoopsie[821]: [21:37:31] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/28
Feb 18 21:37:31 user-ThinkPad-X230 whoopsie[821]: [21:37:31] Network connection may be a paid data plan: /org/freedesktop/NetworkManager/Devices/17
Feb 18 21:37:31 user-ThinkPad-X230 whoopsie[821]: [21:37:31] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/28
Feb 18 21:37:31 user-ThinkPad-X230 whoopsie[821]: [21:37:31] Network connection may be a paid data plan: /org/freedesktop/NetworkManager/Devices/17
Feb 18 21:37:52 user-ThinkPad-X230 whoopsie[821]: [21:37:52] Cannot reach: https://daisy.ubuntu.com
Feb 18 21:38:31 user-ThinkPad-X230 nm-openvpn[15005]: [openvpn-server] Inactivity timeout (--ping-restart), restarting
Feb 18 21:38:31 user-ThinkPad-X230 nm-openvpn[15005]: SIGUSR1[soft,ping-restart] received, process restarting
Feb 18 21:38:33 user-ThinkPad-X230 nm-openvpn[15005]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Feb 18 21:38:33 user-ThinkPad-X230 nm-openvpn[15005]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Feb 18 21:38:33 user-ThinkPad-X230 nm-openvpn[15005]: UDPv4 link local: [undef]
Feb 18 21:38:33 user-ThinkPad-X230 nm-openvpn[15005]: UDPv4 link remote: [AF_INET]148.250.13.121:1194


[COLOR=#000000]
[/COLOR]
```

---

### Post by jason_p2 on 2016-03-10
If you are able to reach local VPN resources on the LAN but not the Internet, this sounds like a network gateway/routing issue on the local client. Make sure your client is getting a default gateway from the VPN and verify in the client's route table (Using route command) that the default is pointing upstream. You could also do a traceroute to an Internet source and see where the traffic is failing.

---

### Post by SeijiSensei on 2016-03-10
Bring up the tunnel, then open a terminal window, run the command "route -n", and post the results here in [noparse]```

```[/noparse] tags.

---

