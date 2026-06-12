---
title: "Trying to run bridged and routed instances of OpenVPN"
date: 2015-07-17
forum: Server Platforms
---

### Post by Luke_Higgs on 2015-07-17
I have one instance (server.conf, configured for port 1193/udp) of openvpn running in bridged mode for desktops and other clients that need to appear to be physically on the network, this is working properly. Since iphones cannot use tap I have a second instance (server02.conf, configured for port 1194/udp) configured for a routed configuration which connects fine but I'm hitting a wall when I uncomment: ```
push "redirect-gateway def1 bypass-dhcp"
``` Connected clients cannot get out to the internet with this uncommented. I don't need mobile devices to access services on the VPN network or subnets behind it but I DO need mobile devices to redirect all network traffic through the VPN for security. I think it must be due to my interfaces bridge configuration. Is it possible to have both open vpn instances running, one using a bridge and another a routed config?

my interfaces file:
```

# The loopback network interfaceauto lo
iface lo inet loopback


auto br0
iface br0 inet static
        address 192.168.3.1
        netmask 255.255.255.192
        gateway 192.168.3.62
        network 192.168.3.0
        broadcast 192.168.3.63
        bridge_ports p4p1
        dns-nameservers 8.8.8.8 8.8.4.4 192.168.1.5 192.168.1.11


iface p4p1 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down

```

server02.conf:
```
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 192.168.4.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.3.0 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
tls-auth ta.key 0 # This file is secret
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
```

Can I run both types of openvpn?

Thanks in advance!

---

### Post by volkswagner on 2015-07-18
I don't see tun adapter in your interface file.
What is output of 
```
ifconfig
```

Also, specifically why is it necessary for laptops to connect with bridge? Properly configured routed vpn works for most everything.
Road warriors may need to get used to not browsing "network neighborhood" but they can connect to mapped drives just as if they
were on the same subnet as LAN (provide you use ip addresses or have working internal DNS). 

Have you tried using push "redirect-gateway def1" (without bypass-dhcp)?

What information does log provide? You may need to turn up verbosity.

---

### Post by Luke_Higgs on 2015-07-18
Thanks for your help, here is ifconfig:
```
br0       Link encap:Ethernet  HWaddr 00:25:90:ae:60:84
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:feae:6084/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7521 (7.5 KB)  TX bytes:17849 (17.8 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:652 (652.0 B)  TX bytes:652 (652.0 B)


p4p1      Link encap:Ethernet  HWaddr 00:25:90:ae:60:84
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8949 (8.9 KB)  TX bytes:18569 (18.5 KB)
          Interrupt:16 Memory:dfc00000-dfc20000


tap0      Link encap:Ethernet  HWaddr fa:da:1f:27:5f:9c
          inet6 addr: fe80::f8da:1fff:fe27:5f9c/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:7810 (7.8 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.4.1  P-t-P:192.168.4.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

I'm not opposed to using a routed configuration however I need connected clients to access resources on other subnets and would prefer the option of administering connected clients as if they were actual hosts. The vpn server is not on the same LAN as the services they need to access and I would like to keep them isolated, if this can be achieved with a routed config then that is fine. I have tried [COLOR=#000000]push "redirect-gateway def1" but same thing happens.

[/COLOR]Thanks,
Luke

---

### Post by volkswagner on 2015-07-18
Please post log for client connecting to vpn (server02.conf).

---

### Post by Luke_Higgs on 2015-07-20
This is the log (verbosity 3) of the client connecting to server02.conf:


```
Mon Jul 20 19:46:42 2015 OpenVPN 2.3.2 x86_64-w64-mingw32 [SSL (OpenSSL)] [LZO] [PKCS11] [eurephia] [IPv6] built on Aug  7 2014
Enter Management Password:
Mon Jul 20 19:46:42 2015 MANAGEMENT: TCP Socket listening on [AF_INET]127.0.0.1:25340
Mon Jul 20 19:46:42 2015 Need hold release from management interface, waiting...
Mon Jul 20 19:46:42 2015 MANAGEMENT: Client connected from [AF_INET]127.0.0.1:25340
Mon Jul 20 19:46:42 2015 MANAGEMENT: CMD 'state on'
Mon Jul 20 19:46:42 2015 MANAGEMENT: CMD 'log all on'
Mon Jul 20 19:46:42 2015 MANAGEMENT: CMD 'hold off'
Mon Jul 20 19:46:42 2015 MANAGEMENT: CMD 'hold release'
Mon Jul 20 19:46:42 2015 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Mon Jul 20 19:46:42 2015 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Jul 20 19:46:42 2015 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Jul 20 19:46:42 2015 Socket Buffers: R=[8192->8192] S=[8192->8192]
Mon Jul 20 19:46:42 2015 UDPv4 link local: [undef]
Mon Jul 20 19:46:42 2015 UDPv4 link remote: [AF_INET]1.2.3.4:1194
Mon Jul 20 19:46:42 2015 MANAGEMENT: >STATE:1437436002,WAIT,,,
Mon Jul 20 19:46:42 2015 MANAGEMENT: >STATE:1437436002,AUTH,,,
Mon Jul 20 19:46:42 2015 TLS: Initial packet from [AF_INET]1.2.3.4:1194, sid=e1ea7b72 d604b42d
Mon Jul 20 19:46:43 2015 VERIFY OK: depth=1, C=US, ST=NC, L=Cary, O=Company Name, OU=DOMAIN-VPN001, CN=Company Name CA, name=EasyRSA, emailAddress=email@address.com
Mon Jul 20 19:46:43 2015 Validating certificate key usage
Mon Jul 20 19:46:43 2015 ++ Certificate has key usage  00a0, expects 00a0
Mon Jul 20 19:46:43 2015 VERIFY KU OK
Mon Jul 20 19:46:43 2015 Validating certificate extended key usage
Mon Jul 20 19:46:43 2015 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Mon Jul 20 19:46:43 2015 VERIFY EKU OK
Mon Jul 20 19:46:43 2015 VERIFY OK: depth=0, C=US, ST=NC, L=Cary, O=Company Name, OU=DOMAIN-VPN001, CN=server, name=EasyRSA, emailAddress=email@address.com
Mon Jul 20 19:46:43 2015 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Jul 20 19:46:43 2015 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Jul 20 19:46:43 2015 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Jul 20 19:46:43 2015 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Jul 20 19:46:43 2015 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mon Jul 20 19:46:43 2015 [server] Peer Connection Initiated with [AF_INET]1.2.3.4:1194
Mon Jul 20 19:46:44 2015 MANAGEMENT: >STATE:1437436004,GET_CONFIG,,,
Mon Jul 20 19:46:45 2015 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Mon Jul 20 19:46:45 2015 PUSH: Received control message: 'PUSH_REPLY,route 192.168.3.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 8.8.8.8,dhcp-option DNS 8.8.4.4,route 192.168.4.0 255.255.255.0,topology net30,ping 10,ping-restart 120,ifconfig 192.168.4.6 192.168.4.5'
Mon Jul 20 19:46:45 2015 OPTIONS IMPORT: timers and/or timeouts modified
Mon Jul 20 19:46:45 2015 OPTIONS IMPORT: --ifconfig/up options modified
Mon Jul 20 19:46:45 2015 OPTIONS IMPORT: route options modified
Mon Jul 20 19:46:45 2015 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Jul 20 19:46:45 2015 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Mon Jul 20 19:46:45 2015 MANAGEMENT: >STATE:1437436005,ASSIGN_IP,,192.168.4.6,
Mon Jul 20 19:46:45 2015 open_tun, tt->ipv6=0
Mon Jul 20 19:46:45 2015 TAP-WIN32 device [Local Area Connection 3] opened: \\.\Global\{48AB0605-3862-48E3-A9F6-3EFC176D0A7A}.tap
Mon Jul 20 19:46:45 2015 TAP-Windows Driver Version 9.9 
Mon Jul 20 19:46:45 2015 Notified TAP-Windows driver to set a DHCP IP/netmask of 192.168.4.6/255.255.255.252 on interface {48AB0605-3862-48E3-A9F6-3EFC176D0A7A} [DHCP-serv: 192.168.4.5, lease-time: 31536000]
Mon Jul 20 19:46:45 2015 Successful ARP Flush on interface [23] {48AB0605-3862-48E3-A9F6-3EFC176D0A7A}
Mon Jul 20 19:46:50 2015 TEST ROUTES: 3/3 succeeded len=2 ret=1 a=0 u/d=up
Mon Jul 20 19:46:50 2015 C:\Windows\system32\route.exe ADD 1.2.3.4 MASK 255.255.255.255 10.1.1.254
Mon Jul 20 19:46:50 2015 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=25 and dwForwardType=4
Mon Jul 20 19:46:50 2015 Route addition via IPAPI succeeded [adaptive]
Mon Jul 20 19:46:50 2015 C:\Windows\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 192.168.4.5
Mon Jul 20 19:46:50 2015 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Mon Jul 20 19:46:50 2015 Route addition via IPAPI succeeded [adaptive]
Mon Jul 20 19:46:50 2015 C:\Windows\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 192.168.4.5
Mon Jul 20 19:46:50 2015 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Mon Jul 20 19:46:50 2015 Route addition via IPAPI succeeded [adaptive]
Mon Jul 20 19:46:50 2015 MANAGEMENT: >STATE:1437436010,ADD_ROUTES,,,
Mon Jul 20 19:46:50 2015 C:\Windows\system32\route.exe ADD 192.168.3.0 MASK 255.255.255.0 192.168.4.5
Mon Jul 20 19:46:50 2015 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Mon Jul 20 19:46:50 2015 Route addition via IPAPI succeeded [adaptive]
Mon Jul 20 19:46:50 2015 C:\Windows\system32\route.exe ADD 192.168.4.0 MASK 255.255.255.0 192.168.4.5
Mon Jul 20 19:46:50 2015 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Mon Jul 20 19:46:50 2015 Route addition via IPAPI succeeded [adaptive]
Mon Jul 20 19:46:50 2015 Initialization Sequence Completed
Mon Jul 20 19:46:50 2015 MANAGEMENT: >STATE:1437436010,CONNECTED,SUCCESS,192.168.4.6,1.2.3.4

```


Here is the syslog:


```
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 TLS: Initial packet from [AF_INET]1.2.3.4:55783, sid=d5ecc909 aac86605
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 VERIFY OK: depth=1, C=US, ST=NC, L=Cary, O=Company Name, OU=DOMAIN-VPN001, CN=Company Name CA, name=EasyRSA, emailAddress=email@address.com
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 VERIFY OK: depth=0, C=US, ST=NC, L=Cary, O=Company Name, OU=DOMAIN-VPN001, CN=laptop01, name=EasyRSA, emailAddress=email@address.com
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jul 20 19:46:43 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jul 20 19:46:44 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Jul 20 19:46:44 VPN001 ovpn-server02[1914]: 1.2.3.4:55783 [laptop01] Peer Connection Initiated with [AF_INET]1.2.3.4:55783
Jul 20 19:46:44 VPN001 ovpn-server02[1914]: MULTI: new connection by client 'laptop01' will cause previous active sessions by this client to be dropped.  Remember to use the --duplicate-cn option if you want multiple clients using the same certificate or username to concurrently connect.
Jul 20 19:46:44 VPN001 ovpn-server02[1914]: MULTI_sva: pool returned IPv4=192.168.4.6, IPv6=(Not enabled)
Jul 20 19:46:44 VPN001 ovpn-server02[1914]: MULTI: Learn: 192.168.4.6 -> laptop01/1.2.3.4:55783
Jul 20 19:46:44 VPN001 ovpn-server02[1914]: MULTI: primary virtual IP for laptop01/1.2.3.4:55783: 192.168.4.6
Jul 20 19:46:46 VPN001 ovpn-server02[1914]: laptop01/1.2.3.4:55783 PUSH: Received control message: 'PUSH_REQUEST'
Jul 20 19:46:46 VPN001 ovpn-server02[1914]: laptop01/1.2.3.4:55783 send_push_reply(): safe_cap=940
Jul 20 19:46:46 VPN001 ovpn-server02[1914]: laptop01/1.2.3.4:55783 SENT CONTROL [laptop01]: 'PUSH_REPLY,route 192.168.3.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 8.8.8.8,dhcp-option DNS 8.8.4.4,route 192.168.4.0 255.255.255.0,topology net30,ping 10,ping-restart 120,ifconfig 192.168.4.6 192.168.4.5' (status=1)
```


Thanks,
Luke

---

### Post by volkswagner on 2015-07-20
Getting back to basics:

When connected to server02 can you ping the server? Can the server ping the client? Can the client ping 8.8.8.8?

Did you setup iptables as described in t [OpenVPN docs]("https://openvpn.net/index.php/open-source/documentation/howto.html") for running "redirect gateway"

```
iptables -t nat -A POSTROUTING -s 192.168.4.0/24 -o eth0 -j MASQUERADE
```

I was a bit surprised to see all those Windows commands in the log. 

From the Windows client, while connected... what does route command yield?

```
route print
```

---

### Post by Luke_Higgs on 2015-07-22
Here is the result of route print on the windows client:
```
===========================================================================Interface List
 23...00 ff 48 ab 06 05 ......TAP-Windows Adapter V9
 14...78 dd 08 b0 f8 b7 ......Bluetooth Device (Personal Area Network)
 12...00 26 c6 0c 72 06 ......Intel(R) WiFi Link 5100 AGN
 11...00 27 13 b7 03 7e ......Intel(R) 82567LM Gigabit Network Connection
  1...........................Software Loopback Interface 1
 21...00 00 00 00 00 00 00 e0 Teredo Tunneling Pseudo-Interface
 22...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #3
 18...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
===========================================================================


IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       10.1.1.254        10.1.1.30    281
          0.0.0.0        128.0.0.0      192.168.4.9     192.168.4.10     30
         10.1.1.0    255.255.255.0         On-link         10.1.1.30    281
        10.1.1.30  255.255.255.255         On-link         10.1.1.30    281
       10.1.1.255  255.255.255.255         On-link         10.1.1.30    281
    12.107.195.27  255.255.255.255       10.1.1.254        10.1.1.30     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
        128.0.0.0        128.0.0.0      192.168.4.9     192.168.4.10     30
      192.168.3.0    255.255.255.0      192.168.4.9     192.168.4.10     30
      192.168.4.0    255.255.255.0      192.168.4.9     192.168.4.10     30
      192.168.4.8  255.255.255.252         On-link      192.168.4.10    286
     192.168.4.10  255.255.255.255         On-link      192.168.4.10    286
     192.168.4.11  255.255.255.255         On-link      192.168.4.10    286
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link      192.168.4.10    286
        224.0.0.0        240.0.0.0         On-link         10.1.1.30    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link      192.168.4.10    286
  255.255.255.255  255.255.255.255         On-link         10.1.1.30    281
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0       10.1.1.254  Default
===========================================================================


IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
  1    306 ::1/128                  On-link
 23    286 fe80::/64                On-link
 12    281 fe80::/64                On-link
 12    281 fe80::14eb:5aff:b0b7:9c07/128
                                    On-link
 23    286 fe80::ecb3:1cb4:7a59:6e14/128
                                    On-link
  1    306 ff00::/8                 On-link
 23    286 ff00::/8                 On-link
 12    281 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None
```

I believe my firewall rules are correct, I am more familiar with managing iptables without ufw on redhat flavors so please bear with me.

/etc/default/ufw:
```

#
# Set to yes to apply rules to support IPv6 (no means only IPv6 on loopback
# accepted). You will need to 'disable' and then 'enable' the firewall for
# the changes to take affect.
IPV6=yes


# Set the default input policy to ACCEPT, DROP, or REJECT. Please note that if
# you change this you will most likely want to adjust your rules.
DEFAULT_INPUT_POLICY="DROP"


# Set the default output policy to ACCEPT, DROP, or REJECT. Please note that if
# you change this you will most likely want to adjust your rules.
DEFAULT_OUTPUT_POLICY="ACCEPT"


# Set the default forward policy to ACCEPT, DROP or REJECT.  Please note that
# if you change this you will most likely want to adjust your rules
DEFAULT_FORWARD_POLICY="ACCEPT"


# Set the default application policy to ACCEPT, DROP, REJECT or SKIP. Please
# note that setting this to ACCEPT may be a security risk. See 'man ufw' for
# details
DEFAULT_APPLICATION_POLICY="SKIP"


# By default, ufw only touches its own chains. Set this to 'yes' to have ufw
# manage the built-in chains too. Warning: setting this to 'yes' will break
# non-ufw managed firewall rules
MANAGE_BUILTINS=no


#
# IPT backend
#
# only enable if using iptables backend
IPT_SYSCTL=/etc/ufw/sysctl.conf


# Extra connection tracking modules to load. Complete list can be found in
# net/netfilter/Kconfig of your kernel source. Some common modules:
# nf_conntrack_irc, nf_nat_irc: DCC (Direct Client to Client) support
# nf_conntrack_netbios_ns: NetBIOS (samba) client support
# nf_conntrack_pptp, nf_nat_pptp: PPTP over stateful firewall/NAT
# nf_conntrack_ftp, nf_nat_ftp: active FTP support
# nf_conntrack_tftp, nf_nat_tftp: TFTP support (server side)

```

/etc/ufw/before.rules:
```
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#


# Don't delete these required lines, otherwise there will be errors
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]


# Forward traffic through eth0 - Change to match you out-interface
-A POSTROUTING -s 192.168.4.0/24 -o p4p1 -j MASQUERADE


*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines




# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT


# quickly process packets for which we already have a connection
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT


# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP


# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT


# ok icmp code for FORWARD
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT


# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT


#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local


# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN


# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN


# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN


# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP


# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT


# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```
/etc/after.rules:
```

## rules.input-after
#
# Rules that should be run after the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-after-input
#   ufw-after-output
#   ufw-after-forward
#


# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-after-input - [0:0]
:ufw-after-output - [0:0]
:ufw-after-forward - [0:0]
# End required lines


# don't log noisy services by default
-A ufw-after-input -p udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 68 -j ufw-skip-to-policy-input


# don't log noisy broadcast
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

Thanks for your help,
Luke

---

### Post by Luke_Higgs on 2015-07-22
I was trying to edit the above post to add this but couldn't...to answer your first question, I can ping 192.168.3.1 (the ip address of the openvpn server) and can ping the client from the server. I cannot ping 8.8.8.8 or other public ip addresses.

Thanks,
Luke

---

### Post by SeijiSensei on 2015-07-22
I presume you've enabled IP packet forwarding by uncommenting
```
net.ipv4.ip_forward=1
```
in /etc/sysctl.conf.  If not, do so, then reboot.  Any better?

---

### Post by Luke_Higgs on 2015-07-24
This is enabled:

net.ipv4.ip_forward=1


Still haven't got it to work, I will have to put this project on hold and might go with another way to secure mobile devices or achieve the same results with routed config but I will update this thread with my solution.

Thanks!
Luke

---

