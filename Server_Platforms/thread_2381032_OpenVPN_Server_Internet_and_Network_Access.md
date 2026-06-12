---
title: "OpenVPN Server Internet and Network Access"
date: 2017-12-25
forum: Server Platforms
---

### Post by fabiansc on 2017-12-25
Hello everybody.

I was unable to post everything in one post with Safari and Chrome. I received an error regarding some missing security token. Therefore I was forced to split my question and some information into several posts until it was working.

Thanks for your understanding!

---

### Post by fabiansc on 2017-12-25
Hello everyone!

I have been playing around with Ubuntu for a while now and tried out some projects, e.g. by leveraging [Ubuntu MAAS]("https://cloud.fas-consulting.de/drupal/page/cloud-computing/metal-service-maas"). Right now I would like to continue to play with Ubuntu MAAS and a virtualized infrastructure, which VMs are installed via Ubuntu MAAS. Therefore I need to connect to the VMware ESXI Hypervisor running on my bare metal. To do so, I wanted to utilize OpenVPN running on a Raspberry Pi 3. And here starts my issues, as I am unable to connect to the internet once connected via OpenVPN (all traffic should go through the RPi). OpenVPN Clients should be able to access the internet via the Gateway behind the Raspberry Pi and the MAAS network 192.168.200.0/24.

I am currently using MacOS to play around and get it working. Any help to get it working is highly appreciated!

---

### Post by fabiansc on 2017-12-25
[B]Network
[/B]
RPi Ubuntu MAAS Link (192.168.200.1@eth0)
RPi Internet Uplink (192.168.190.100@wlan0) via 192.168.190.1 (Gateway router)
RPi OpenVPN Server (10.8.0.1@tun0)

```

[COLOR=#000000][FONT=Menlo]enxb827ebf3bacf Link encap:Ethernet  HWaddr b8:27:eb:f3:ba:cf  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet addr:192.168.200.1  Bcast:192.168.200.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet6 addr: fe80::d938:9ec1:e42d:a689/64 Scope:Link[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX packets:3604 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          TX packets:38591 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX bytes:578338 (578.3 KB)  TX bytes:5457841 (5.4 MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX packets:2609741 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          TX packets:2609741 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          collisions:0 txqueuelen:1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX bytes:1031530481 (1.0 GB)  TX bytes:1031530481 (1.0 GB)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet6 addr: fe80::9e4b:b693:b6dd:3c9e/64 Scope:Link[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX packets:1086 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          TX packets:334 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          collisions:0 txqueuelen:100 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX bytes:84855 (84.8 KB)  TX bytes:48942 (48.9 KB)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0     Link encap:Ethernet  HWaddr b8:27:eb:a6:ef:9a  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet addr:192.168.190.100  Bcast:192.168.190.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          inet6 addr: fe80::99b:acee:f4e0:9d58/64 Scope:Link[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX packets:79650 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          TX packets:51909 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          RX bytes:42541442 (42.5 MB)  TX bytes:8717906 (8.7 MB)[/FONT][/COLOR]

```

Once everything has been set up I can connect from a different location (192.168.180.x) via the internet (different sub-nets) to the OpenVPN Server. Once this happens no connectivity to the internet is possible for my client (192.168.180.x). But I can ping all NICs of the Raspberry Pi from the client:

```

[COLOR=#000000][FONT=Menlo]fabiansc$ ping 10.8.0.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PING 10.8.0.1 (10.8.0.1): 56 data bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]64 bytes from 10.8.0.1: icmp_seq=0 ttl=64 time=51.012 ms

[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]fabiansc$ ping 192.168.190.100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PING 192.168.190.100 (192.168.190.100): 56 data bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]64 bytes from 192.168.190.100: icmp_seq=0 ttl=64 time=56.354 ms

[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]abiansc$ ping 192.168.200.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PING 192.168.200.1 (192.168.200.1): 56 data bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]64 bytes from 192.168.200.1: icmp_seq=0 ttl=64 time=84.131 ms[/FONT][/COLOR]

```

If I ping networks behind the Raspberry Pi the client receive timeouts:

```

[COLOR=#000000][FONT=Menlo]fabiansc$ ping 192.168.190.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PING 192.168.190.1 (192.168.190.1): 56 data bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Request timeout for icmp_seq 0[/FONT][/COLOR]

```

*Traceroutes* redirect traffic to 10.8.0.1; afterwards everything gets lost.

---

### Post by fabiansc on 2017-12-25
**OpenVPN Server.conf**
```

[COLOR=#5230E1][FONT=Menlo]#################################################[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Sample OpenVPN 2.0 config file for            #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# multi-client server.                          #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#                                               #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# This file is for the server side              #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# of a many-clients <-> one-server              #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# OpenVPN configuration.                        #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#                                               #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# OpenVPN also supports                         #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# single-machine <-> single-machine             #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# configurations (See the Examples page         #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# on the web site for more info).               #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#                                               #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# This config should work on Windows            #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# or Linux/BSD systems.  Remember on            #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Windows to quote pathnames and use            #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# double backslashes, e.g.:                     #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# "C:\\Program Files\\OpenVPN\\config\\foo.key" #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#                                               #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Comments are preceded with '#' or ';'         #[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#################################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Which local IP address should OpenVPN[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# listen on? (optional)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];local a.b.c.d[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Which TCP/UDP port should OpenVPN listen on?[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# If you want to run multiple OpenVPN instances[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# on the same machine, use a different port[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# number for each one.  You will need to[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# open up this port on your firewall.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]port 1194[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# TCP or UDP server?[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]proto tcp[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];proto udp[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# "dev tun" will create a routed IP tunnel,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# "dev tap" will create an ethernet tunnel.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Use "dev tap0" if you are ethernet bridging[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and have precreated a tap0 virtual interface[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and bridged it with your ethernet interface.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# If you want to control access policies[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# over the VPN, you must create firewall[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# rules for the the TUN/TAP interface.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# On non-Windows systems, you can give[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# an explicit unit number, such as tun0.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# On Windows, use "dev-node" for this.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# On most systems, the VPN will not function[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# unless you partially or fully disable[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the firewall for the TUN/TAP interface.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];dev tap[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]dev tun[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Windows needs the TAP-Win32 adapter name[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# from the Network Connections panel if you[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# have more than one.  On XP SP2 or higher,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# you may need to selectively disable the[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Windows firewall for the TAP adapter.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Non-Windows systems usually don't need this.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];dev-node MyTap[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# SSL/TLS root certificate (ca), certificate[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# (cert), and private key (key).  Each client[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and the server must have their own cert and[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# key file.  The server and all clients will[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# use the same ca file.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# See the "easy-rsa" directory for a series[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# of scripts for generating RSA certificates[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and private keys.  Remember to use[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# a unique Common Name for the server[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and each of the client certificates.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Any X509 key management system can be used.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# OpenVPN can also use a PKCS #12 formatted key file[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# (see "pkcs12" directive in man page).[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ca ca.crt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]cert Nexus-OpenVPN.crt[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo][COLOR=#000000]key Nexus-OpenVPN.key  [/COLOR]# This file should be kept secret[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Diffie hellman parameters.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Generate your own with:[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#   openssl dhparam -out dh2048.pem 2048[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]dh dh2048.pem[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Network topology[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Should be subnet (addressing via IP)[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# unless Windows clients v2.0.9 and lower have to[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# be supported (then net30, i.e. a /30 per client)[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Defaults to net30 (not recommended)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]topology subnet[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Configure server mode and supply a VPN subnet[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# for OpenVPN to draw client addresses from.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# The server will take 10.8.0.1 for itself,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the rest will be made available to clients.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Each client will be able to reach the server[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# on 10.8.0.1. Comment this line out if you are[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# ethernet bridging. See the man page for more info.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]server 10.8.0.0 255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Maintain a record of client <-> virtual IP address[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# associations in this file.  If OpenVPN goes down or[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# is restarted, reconnecting clients can be assigned[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the same virtual IP address from the pool that was[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# previously assigned.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ifconfig-pool-persist ipp.txt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Configure server mode for ethernet bridging.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# You must first use your OS's bridging capability[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to bridge the TAP interface with the ethernet[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# NIC interface.  Then you must manually set the[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# IP/netmask on the bridge interface, here we[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# assume 10.8.0.4/255.255.255.0.  Finally we[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# must set aside an IP range in this subnet[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# (start=10.8.0.50 end=10.8.0.100) to allocate[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to connecting clients.  Leave this line commented[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# out unless you are ethernet bridging.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Configure server mode for ethernet bridging[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# using a DHCP-proxy, where clients talk[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to the OpenVPN server-side DHCP server[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to receive their IP address allocation[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and DNS server addresses.  You must first use[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# your OS's bridging capability to bridge the TAP[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# interface with the ethernet NIC interface.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Note: this mode only works on clients (such as[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Windows), where the client-side TAP adapter is[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# bound to a DHCP client.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];server-bridge[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Push routes to the client to allow it[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to reach other private subnets behind[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the server.  Remember that these[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# private subnets will also need[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to know to route the OpenVPN client[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# address pool (10.8.0.0/255.255.255.0)[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# back to the OpenVPN server.[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]push [/COLOR]"route 192.168.190.0 255.255.255.0"[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]push [/COLOR]"route 192.168.200.0 255.255.255.0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# To assign specific IP addresses to specific[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# clients or if a connecting client has a private[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# subnet behind it that should also have VPN access,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# use the subdirectory "ccd" for client-specific[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# configuration files (see man page for more info).[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# EXAMPLE: Suppose the client[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# having the certificate common name "Thelonious"[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# also has a small subnet behind his connecting[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# machine, such as 192.168.40.128/255.255.255.248.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# First, uncomment out these lines:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];client-config-dir ccd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];route 192.168.40.128 255.255.255.248[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]route 10.8.0.0 255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Then create a file ccd/Thelonious with this line:[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#   iroute 192.168.40.128 255.255.255.248[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# This will allow Thelonious' private subnet to[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# access the VPN.  This example will only work[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# if you are routing, not bridging, i.e. you are[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# using "dev tun" and "server" directives.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# EXAMPLE: Suppose you want to give[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Thelonious a fixed VPN IP address of 10.9.0.1.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# First uncomment out these lines:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];client-config-dir ccd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];route 10.9.0.0 255.255.255.252[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Then add this line to ccd/Thelonious:[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#   ifconfig-push 10.9.0.1 10.9.0.2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Suppose that you want to enable different[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# firewall access policies for different groups[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# of clients.  There are two methods:[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# (1) Run multiple OpenVPN daemons, one for each[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#     group, and firewall the TUN/TAP interface[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#     for each group/daemon appropriately.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# (2) (Advanced) Create a script to dynamically[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#     modify the firewall in response to access[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#     from different clients.  See man[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#     page for more info on learn-address script.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];learn-address ./script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# If enabled, this directive will configure[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# all clients to redirect their default[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# network gateway through the VPN, causing[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# all IP traffic such as web browsing and[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and DNS lookups to go through the VPN[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# (The OpenVPN server machine may need to NAT[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# or bridge the TUN/TAP interface to the internet[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# in order for this to work properly).[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]push [/COLOR]"redirect-gateway def1 bypass-dhcp"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Certain Windows-specific network settings[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# can be pushed to clients, such as DNS[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# or WINS server addresses.  CAVEAT:[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# http://openvpn.net/faq.html#dhcpcaveats[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# The addresses below refer to the public[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# DNS servers provided by opendns.com.[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]push [/COLOR]"dhcp-option DNS 208.67.222.222"[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]push [/COLOR]"dhcp-option DNS 208.67.220.220"[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000];push [/COLOR]"dhcp-option DNS 8.8.8.8"[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000];push [/COLOR]"dhcp-option DNS 8.8.4.4"

[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Uncomment this directive to allow different[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# clients to be able to "see" each other.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# By default, clients will only see the server.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# To force clients to only see the server, you[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# will also need to appropriately firewall the[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# server's TUN/TAP interface.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];client-to-client[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Uncomment this directive if multiple clients[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# might connect with the same certificate/key[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# files or common names.  This is recommended[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# only for testing purposes.  For production use,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# each client should have its own certificate/key[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# pair.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# IF YOU HAVE NOT GENERATED INDIVIDUAL[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# CERTIFICATE/KEY PAIRS FOR EACH CLIENT,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# EACH HAVING ITS OWN UNIQUE "COMMON NAME",[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# UNCOMMENT THIS LINE OUT.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];duplicate-cn[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# The keepalive directive causes ping-like[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# messages to be sent back and forth over[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the link so that each side knows when[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the other side has gone down.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Ping every 10 seconds, assume that remote[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# peer is down if no ping received during[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# a 120 second time period.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]keepalive 10 120[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# For extra security beyond that provided[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# by SSL/TLS, create an "HMAC firewall"[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# to help block DoS attacks and UDP port flooding.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Generate with:[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#   openvpn --genkey --secret ta.key[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# The server and each client must have[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# a copy of this key.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# The second parameter should be '0'[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# on the server and '1' on the clients.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo][COLOR=#000000]tls-auth ta.key 0 [/COLOR]# This file is secret[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]key-direction 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Select a cryptographic cipher.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# This config item must be copied to[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the client config file as well.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];cipher BF-CBC        [COLOR=#5230E1]# Blowfish (default)[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]cipher AES-128-CBC   [COLOR=#5230E1]# AES[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];cipher DES-EDE3-CBC  [COLOR=#5230E1]# Triple-DES[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth SHA256[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Enable compression on the VPN link.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# If you enable it here, you must also[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# enable it in the client config file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]comp-lzo[/FONT][/COLOR]

[COLOR=#5230E1][FONT=Menlo]# The maximum number of concurrently connected[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# clients we want to allow.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];max-clients 100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# It's a good idea to reduce the OpenVPN[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# daemon's privileges after initialization.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# You can uncomment this out on[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# non-Windows systems.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]user nobody[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]group nogroup[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# The persist options will try to avoid[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# accessing certain resources on restart[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# that may no longer be accessible because[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# of the privilege downgrade.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]persist-key[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]persist-tun[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Output a short status file showing[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# current connections, truncated[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# and rewritten every minute.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]status openvpn-status.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# By default, log messages will go to the syslog (or[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# on Windows, if running as a service, they will go to[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# the "\Program Files\OpenVPN\log" directory).[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Use log or log-append to override this default.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# "log" will truncate the log file on OpenVPN startup,[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# while "log-append" will append to it.  Use one[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# or the other (but not both).[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];log         openvpn.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];log-append  openvpn.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Set the appropriate level of log[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# file verbosity.[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# 0 is silent, except for fatal errors[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# 4 is reasonable for general usage[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# 5 and 6 can help to debug connection problems[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# 9 is extremely verbose[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]verb 3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Silence repeating messages.  At most 20[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# sequential messages of the same message[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# category will be output to the log.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo];mute 20[/FONT][/COLOR]



```

**OpenVPN Client.conf**

```

##############################################
# Sample client-side OpenVPN 2.0 config file #
# for connecting to multi-client server.     #
#                                            #
# This configuration can be used by multiple #
# clients, however each client should have   #
# its own cert and key files.                #
#                                            #
# On Windows, you might want to rename this  #
# file so it has a .ovpn extension           #
##############################################


# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client


# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun


# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap


# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
proto tcp
;proto udp


# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote cloud.fas-consulting.de 1194
;remote my-server-2 1194


# Choose a random host from the remote
# list for load-balancing.  Otherwise
# try hosts in the order specified.
;remote-random


# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite


# Most clients don't need to bind to
# a specific local port number.
nobind


# Downgrade privileges after initialization (non-Windows only)
user nobody
group nogroup


# Try to preserve some state across restarts.
persist-key
persist-tun


# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here.  See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]


# Wireless networks often produce a lot
# of duplicate packets.  Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings


# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
#ca ca.crt        # Added within file
#cert client.crt    # Added within file
#key client.key        # Added within file


# Verify server certificate by checking that the
# certicate has the correct key usage set.
# This is an important precaution to protect against
# a potential attack discussed here:
#  http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the keyUsage set to
#   digitalSignature, keyEncipherment
# and the extendedKeyUsage to
#   serverAuth
# EasyRSA can do this for you.
remote-cert-tls server


# If a tls-auth key is used on the server
# then every client must also have the key.
;tls-auth ta.key 1


# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
cipher AES-128-CBC
auth SHA256


key-direction 1


# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo


# Set log file verbosity.
verb 3


# Silence repeating messages
;mute 20




# Linux Client configuration for resolvconf utilitiy. 
# This updates DNS information for Linux clients.
# script-security 2
# up /etc/openvpn/update-resolv-conf
# down /etc/openvpn/update-resolv-conf
<ca>
...
</ca>
<cert>
...
</cert>
<key>
...
</key>
<tls-auth>
...
</tls-auth>

```

---

### Post by darkod on 2017-12-25
Too much text and info, lets get little specific and short...

1. Where is the ESXi running, on which machine/network?
2. From the remote site (192.168.180.x) you need only to connect to the ESXi, you don't need anything else?

Answer this so we can try helping.

---

### Post by fabiansc on 2017-12-25
Hi Darko,

thanks for the quick reply.

ESXi is running on 192.168.200.10 (static ip provided by Ubuntu MAAS DHCP; running in parallel with the OpenVPN Server on the same host).


I want to connect from 192.168.180.x to 10.8.0.1 (192.168.190.100; static ip provided by 192.168.190.1 / Router) and its internet via 192.168.190.1.
I also want to connect from 192.168.180.x via 10.8.0.1 (192.168.200.1) to 192.168.200.10 (ESXi and its VMs of 192.168.200.100-199).

---

### Post by darkod on 2017-12-25
OK, here is what I suggest...

1. First, instead of using the whole sample server.conf and client.conf files, copy and paste only the parameters that you need to use. That makes your server.conf and client.conf much more easily readable for all, you and us...

2. If you only need to connect from the remote site to the OpenVPN server and the ESXi, you don't need to use the parameter to route all client traffic through the vpn. I would delete that parameter from the openvpn server.conf and restart openvpn. Clients can always reach the openvpn server even without that parameter. Use only the necessary vpn config. Routing all traffic through vpn is not needed if you only need to access few resources on the vpn side. In fact you might get unexpected results or traffic delay by routing everything through a vpn.

3. To be able to reach the ESXi on 192.168.200.10 you need to enable forwarding on the openvpn server. The rest seems to be OK because you are pushing the necessary rputes already in your server.conf. To enable forwarding:
3a. Open /etc/sysctl.conf on the openvpn server and enable the ipv4_forward parameter. Reboot it to take effect.
3b. Run this (temporary) iptables rule to check if ESXi connectivity will work:
```
sudo iptables -A POSTROUTING -o eth0 -j MASQUERADE
```
Can you connect now to the ESXi from the vpn client?

Of coure the above assumes there are no internal firewalls or any strange routing inside the LANs. It should work...

---

### Post by fabiansc on 2017-12-25
Hi Darko,

I commented-out the network redirect from my server.conf.

```
;push "redirect-gateway def1 bypass-dhcp"

```

ipv4 was already enabled for forwarding:

```
[COLOR=#000000][FONT=Menlo]# Uncomment the next line to enable packet forwarding for IPv4[/FONT][/COLOR]
[COLOR=#33BBC8][FONT=Menlo]net.ipv4.ip_forward[COLOR=#CD7923]=[/COLOR][COLOR=#C33720]1
[/COLOR][/FONT][/COLOR]

```

Updating the IP Table results in an error; any idea (-t nat missing?):
```

[COLOR=#000000][FONT=Menlo]fabiansc@Nexus:~$ sudo iptables -A POSTROUTING -o enxb827ebf3bacf -j MASQUERADE[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]iptables: No chain/target/match by that name.[/FONT][/COLOR]

```

I guess this blocks network traffic to reach my client:
```

client:~ fabiansc$ traceroute 192.168.200.10
traceroute to 192.168.200.10 (192.168.200.10), 64 hops max, 52 byte packets
 1  10.8.0.1 (10.8.0.1)  99.635 ms  47.844 ms  50.412 ms
 2  * * *

```


This also does not work:
```

[COLOR=#000000][FONT=Menlo]fabiansc@Nexus:~$ sudo iptables -t nat -A POSTROUTING -o enxb827ebf3bacf -j MASQUERADE[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]client:~ fabiansc$ ping 192.168.200.10[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PING 192.168.200.10 (192.168.200.10): 56 data bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Request timeout for icmp_seq 0
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]fabiansc$ traceroute 192.168.200.10[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]traceroute to 192.168.200.10 (192.168.200.10), 64 hops max, 52 byte packets[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 1  10.8.0.1 (10.8.0.1)  48.259 ms  46.609 ms  48.479 ms[/FONT][/COLOR]

```

Please note that I have an existing configuration to forward traffic from Ubuntu MAAS VMs to the internet (there is a Bug in Ubuntu MAAS which requires internet access to commission items).

```
fabiansc@Nexus:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level warning


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by darkod on 2017-12-26
Sorry, my mistake. I forgot the '-t nat' in the iptables command. That is the correct one, like you posted it with the '-t nat' included.

The openvpn server is the RPi, right? According to the traceroute from the client, the first hop is correct (10.8.0.1) so it sends the traffic over the vpn tunnel as it should. But then in the openvpn server (RPi?) it stops. Which points to the forwarding settings in the openvpn server. So, please post the following from your openvpn server:
```
sudo iptables -L -n -v
sudo iptables -t nat -L -n -v
```

That will show us the rules in both the filter chain and nat chain.

---

### Post by fabiansc on 2017-12-26
Yep, the RPi is the OpenVPN Server (also Ubuntu MAAS Server with traffic forwarding for MAAS nodes; this works).

```
[COLOR=#000000][FONT=Menlo]fabiansc@Nexus:~$ sudo iptables -L -n -v[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][sudo] password for fabiansc: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain INPUT (policy ACCEPT 1349K packets, 552M bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain FORWARD (policy DROP 174 packets, 11096 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    0     0 ACCEPT     all  --  eth0   eth1    0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    0     0 ACCEPT     all  --  eth1   eth0    0.0.0.0/0            0.0.0.0/0           [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  174 11096 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain OUTPUT (policy ACCEPT 1342K packets, 534M bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo]   

[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]fabiansc@Nexus:~$ sudo iptables -t nat -L -n -v[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain PREROUTING (policy ACCEPT 131 packets, 29802 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain INPUT (policy ACCEPT 101 packets, 27782 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain OUTPUT (policy ACCEPT 2795 packets, 205K bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Chain POSTROUTING (policy ACCEPT 2701 packets, 181K bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] pkts bytes target     prot opt in     out     source               destination         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    0     0 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   94 24399 MASQUERADE  all  --  *      enxb827ebf3bacf  0.0.0.0/0            0.0.0.0/0 [/FONT][/COLOR]

```


Why does those configs contain **eth0**? My eth0 should be **[COLOR=#000000][FONT=Menlo]enxb827ebf3bac[/FONT][/COLOR]**[FONT=Menlo][COLOR=#000000]. I had that strange interface name for all my Raspberry Pis so far. If there is no need to adjust the interface name, we can skip this side-question as it might not be related to this topic.[/COLOR][/FONT]

---

### Post by darkod on 2017-12-26
There is the problem... In the RPi you have the FORWARD policy to DROP and you allow traffic only between eth0 and eth1. The vpn tunnel is tun0 so because it doesn't have an ACCEPT rule, it drops all traffic. Don't forget, vpn traffic uses tun0 and not eth0/eth1 (it uses the virtual interface, not the physical). This is why your client internet was not working when the RPi was gateway also.

Try this on the RPi:
```
sudo iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT (here use the correct eth0 or eth1 depending which subnet you want to forward to)
sudo iptables -A FORWARD -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

If that works you will need to make these rules permanent and also the MASQUERADE rule in -t nat needs to be permanent.

Personally I would do the FORWARD related and established rule little different. I see you are limiting it by both incoming and outgoing interface. I would simple allow all related and established traffic. Otherwise you get into situations like this when things are not working as expected and you waste time troubleshooting to find it.

The important protection is for NEW traffic. After that, ESTABLISHED and RELATED traffic should be allowed to flow... The rule I use on my vpn servers is:
```
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
```

This doesn't care about interfaces. I limit the NEW traffic and let it flow afterwards...

---

### Post by fabiansc on 2017-12-26
Thanks a lot now it is working out.

Here is a summary of the required changes:

```

sudo iptables -t nat -A POSTROUTING -o enxb827ebf3bacf -j MASQUERADE
sudo iptables -A FORWARD -i tun0 -o enxb827ebf3bacf -j ACCEPT
sudo iptables -A FORWARD -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

For my forwarding rules I configured a [script]("https://cloud.fas-consulting.de/drupal/page/cloud-computing/metal-service-maas/maas-operating-system-configuration"), which is based on an [ubuntu recommendation]("https://help.ubuntu.com/community/Router#Enable_IP_forwarding_and_Masquerading"). If I understood you correctly I should adjust the script as followed; can you confirm this. As it is called when booting, it should be automatically triggered. Please note that I noticed that EXTIF and INTIF were eth0 and eth1, which I corrected below (working):

```
EXTIF="wlan0"                   # Internet Uplink
INTIF="enxb827ebf3bacf"         # Intranet (MAAS nodes)
echo"1"> /proc/sys/net/ipv4/ip_forward
echo"1"> /proc/sys/net/ipv4/ip_dynaddr


iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
-A POSTROUTING -o "$INTIF" -j MASQUERADE

COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
-A FORWARD -i tun0 -o "$INTIF" -j ACCEPT
-A FORWARD -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
COMMIT
EOF
```

---

### Post by darkod on 2017-12-26
Yes, it should work. Although I have to add that the last FORWARD rule about ESTABLISHED,RELATED is replacing the above rules related to the same thing. That last rule is not linked to any interface so it covers all. You can delete the other two ESTABLISHED,RELATED if you want to, to make things cleaner... It should still work.

---

### Post by fabiansc on 2017-12-26
Thanks again Darkod.

We got it working. I updated the NAT script as followed (summary for other users), which enables routing for traffic back to OpenVPN users (and therefore resolves my issue):

```
iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
-A POSTROUTING -o "$INTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
-A FORWARD -i tun0 -o "$INTIF" -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
COMMIT
EOF

```

---

