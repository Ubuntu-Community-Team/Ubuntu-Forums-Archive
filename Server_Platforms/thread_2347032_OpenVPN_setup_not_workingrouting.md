---
title: "OpenVPN setup not working/routing"
date: 2016-12-20
forum: Server Platforms
---

### Post by jonobr on 2016-12-20
HI All

I am implementing a new solution for openvpn and I going around the bend.... completely loopy looking at all these configs

The setup is simple really, and I am confused why I cant get this to work. I must be missing something obvious.
I need to create a routed network connecting multiple remote clients to a Open VPN server.
For the client I will be using raspberry pi with two ethernet interfaces one of which is connected to only one box.

The clients networks dont need to go any further then the server , so again, it should be simple
The tunnel gets establish and all looks ready to work, I just cant figure where I am going wrong

I have ip forwarding on on the server and the client and no rules on the firewall that would block

Here is the setup and the problem

[ATTACH=CONFIG]272792[/ATTACH]

AS you can see pinging seems to be working well but not from end to end.
Using iproute on the pi it seems know where to go

```

root@raspberrypi:/home/pi# ip route get 10.8.0.1
10.8.0.1 via 10.8.0.5 dev tun0  src 10.8.0.6
    cache
root@raspberrypi:/home/pi#

```


I am posting netstat -rn on the pi and on the server end as well as my configs.
I am guessing I am missing a static route somewhere


Client routing info

```

root@raspberrypi:/home/pi# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
10.2.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.8.0.1        10.8.0.5        255.255.255.255 UGH       0 0          0 tun0
10.8.0.5        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0


root@raspberrypi:/home/pi#
root@raspberrypi:/home/pi# ifconfig
eth0      Link encap:Ethernet  HWaddr b8:27:eb:cf:91:6b
          inet addr:192.168.0.31  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b66e:de55:11f9:b6c8/64 Scope:Link
          inet6 addr: 2601:640:8302:d1e0:7e16:9051:9329:6eb3/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41379 errors:0 dropped:25 overruns:0 frame:0
          TX packets:24023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6140207 (5.8 MiB)  TX bytes:3160238 (3.0 MiB)

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:70:53:df
          inet addr:10.2.255.2  Bcast:10.2.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13577 errors:0 dropped:1076 overruns:0 frame:0
          TX packets:2477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1064746 (1.0 MiB)  TX bytes:360242 (351.7 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:4156 (4.0 KiB)  TX bytes:4156 (4.0 KiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:104 (104.0 B)  TX bytes:164 (164.0 B)

wlan0     Link encap:Ethernet  HWaddr b8:27:eb:9a:c4:3e
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:2 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:246 (246.0 B)  TX bytes:0 (0.0 B)

root@raspberrypi:/home/pi#

```

Sever routing info
```

root@Sever/etc/openvpn# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
10.1.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
root@Server:/etc/openvpn# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:67:ed:d0:f8
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:67ff:feed:d0f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:353264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37820925 (36.0 MiB)  TX bytes:68714774 (65.5 MiB)
          Memory:b1200000-b127ffff

eth1      Link encap:Ethernet  HWaddr 00:1e:67:ed:d0:f9
          inet addr:10.1.255.254  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21e:67ff:feed:d0f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1668575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2427340 (2.3 MiB)  TX bytes:70080462 (66.8 MiB)
          Memory:b1100000-b117ffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:70121069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70121069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:30362434103 (28.2 GiB)  TX bytes:30362434103 (28.2 GiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:104 (104.0 B)  TX bytes:104 (104.0 B)


```




Any info would be very useful!
```
root@Server:/etc/openvpn# cat server.conf
#################################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients  one-server                 #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine  single-machine                #
# configurations (See the Examples page         #
# on the web site for more info).               #
#                                               #
# This config should work on Windows            #
# or Linux/BSD systems.  Remember on            #
# Windows to quote pathnames and use            #
# double backslashes, e.g.:                     #
# "C:\\Program Files\\OpenVPN\\config\\foo.key" #
#                                               #
# Comments are preceded with '#' or ';'         #
#################################################

# Which local IP address should OpenVPN
# listen on? (optional)
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
proto udp
;proto udp

# "dev tun" will create a routed IP tunnel,
# "dev tap" will create an ethernet tunnel.
# Use "dev tap0" if you are ethernet bridging
# and have precreated a tap0 virtual interface
# and bridged it with your ethernet interface.
# If you want to control access policies
# over the VPN, you must create firewall
# rules for the the TUN/TAP interface.
# On non-Windows systems, you can give
# an explicit unit number, such as tun0.
# On Windows, use "dev-node" for this.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Windows adapter name
# from the Network Connections panel if you
# have more than one.  On XP SP2 or higher,
# you may need to selectively disable the
# Windows firewall for the TAP adapter.
# Non-Windows systems usually don't need this.
;dev-node MyTap

# SSL/TLS root certificate (ca), certificate
# (cert), and private key (key).  Each client
# and the server must have their own cert and
# key file.  The server and all clients will
# use the same ca file.
#
# See the "easy-rsa" directory for a series
# of scripts for generating RSA certificates
# and private keys.  Remember to use
# a unique Common Name for the server
# and each of the client certificates.
#
# Any X509 key management system can be used.
# OpenVPN can also use a PKCS #12 formatted key file
# (see "pkcs12" directive in man page).
ca /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/ca.crt
cert /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/server.crt
key /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys.
dh /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

# Maintain a record of client  virtual IP address
# associations in this file.  If OpenVPN goes down or
# is restarted, reconnecting clients can be assigned
# the same virtual IP address from the pool that was
# previously assigned.
ifconfig-pool-persist ipp.txt

# Configure server mode for ethernet bridging.
# You must first use your OS's bridging capability
# to bridge the TAP interface with the ethernet
# NIC interface.  Then you must manually set the
# IP/netmask on the bridge interface, here we
# assume 10.8.0.4/255.255.255.0.  Finally we
# must set aside an IP range in this subnet
# (start=10.8.0.50 end=10.8.0.100) to allocate
# to connecting clients.  Leave this line commented
# out unless you are ethernet bridging.
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
;push "route 10.1.0.0 255.255.0"
;push "route 192.168.20.0 255.255.255.0"
;route 10.1.0.0 255.255.0.0
;push "route 10.2.0.0 255.255.0.0"
;client-to-client

# To assign specific IP addresses to specific
# clients or if a connecting client has a private
# subnet behind it that should also have VPN access,
# use the subdirectory "ccd" for client-specific
# configuration files (see man page for more info).

# EXAMPLE: Suppose the client
# having the certificate common name "Thelonious"
# also has a small subnet behind his connecting
# machine, such as 192.168.40.128/255.255.255.248.
# First, uncomment out these lines:
;client-config-dir ccd
;route 10.2.255.2 255.255.0.0
# Then create a file ccd/Thelonious with this line:
#   iroute 192.168.40.128 255.255.255.248
# This will allow Thelonious' private subnet to
# access the VPN.  This example will only work
# if you are routing, not bridging, i.e. you are
# using "dev tun" and "server" directives.

# EXAMPLE: Suppose you want to give
# Thelonious a fixed VPN IP address of 10.9.0.1.
# First uncomment out these lines:
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
# Then add this line to ccd/Thelonious:
#   ifconfig-push 10.9.0.1 10.9.0.2

# Suppose that you want to enable different
# firewall access policies for different groups
# of clients.  There are two methods:
# (1) Run multiple OpenVPN daemons, one for each
#     group, and firewall the TUN/TAP interface
#     for each group/daemon appropriately.
# (2) (Advanced) Create a script to dynamically
#     modify the firewall in response to access
#     from different clients.  See man
#     page for more info on learn-address script.
;learn-address ./script

# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway local def1"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
;push "dhcp-option DNS 10.8.0.1"
;push "dhcp-option WINS 10.8.0.1"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
;client-to-client

# Uncomment this directive if multiple clients
# might connect with the same certificate/key
# files or common names.  This is recommended
# only for testing purposes.  For production use,
# each client should have its own certificate/key
# pair.
#
# IF YOU HAVE NOT GENERATED INDIVIDUAL
# CERTIFICATE/KEY PAIRS FOR EACH CLIENT,
# EACH HAVING ITS OWN UNIQUE "COMMON NAME",
# UNCOMMENT THIS LINE OUT.
;duplicate-cn

# The keepalive directive causes ping-like
# messages to be sent back and forth over
# the link so that each side knows when
# the other side has gone down.
# Ping every 10 seconds, assume that remote
# peer is down if no ping received during
# a 120 second time period.
keepalive 10 120

# For extra security beyond that provided
# by SSL/TLS, create an "HMAC firewall"
# to help block DoS attacks and UDP port flooding.
#
# Generate with:
#   openvpn --genkey --secret ta.key
#
# The server and each client must have
# a copy of this key.
# The second parameter should be '0'
# on the server and '1' on the clients.
;tls-auth ta.key 0 # This file is secret

# Select a cryptographic cipher.
# This config item must be copied to
# the client config file as well.
;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

# Enable compression on the VPN link.
# If you enable it here, you must also
# enable it in the client config file.
comp-lzo

# The maximum number of concurrently connected
# clients we want to allow.
max-clients 300

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
;user nobody
;group nobody

# The persist options will try to avoid
# accessing certain resources on restart
# that may no longer be accessible because
# of the privilege downgrade.
persist-key
persist-tun

# Output a short status file showing
# current connections, truncated
# and rewritten every minute.
status openvpn-status.log

# By default, log messages will go to the syslog (or
# on Windows, if running as a service, they will go to
# the "\Program Files\OpenVPN\log" directory).
# Use log or log-append to override this default.
# "log" will truncate the log file on OpenVPN startup,
# while "log-append" will append to it.  Use one
# or the other (but not both).
;log         openvpn.log
;log-append  openvpn.log

# Set the appropriate level of log
# file verbosity.
#
# 0 is silent, except for fatal errors
# 4 is reasonable for general usage
# 5 and 6 can help to debug connection problems
# 9 is extremely verbose
verb 3

# Silence repeating messages.  At most 20
# sequential messages of the same message
# category will be output to the log.
;mute 20

```


Here is the client


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
proto udp
;proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
;remote my-server-2 1194
remote  x.x.x.x 1194 #removed to hid the public IP

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
;user nobody
;group nogroup

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
mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca /usr/share/doc/openvpn/ca.crt
cert /usr/share/doc/openvpn/client1.crt
key /usr/share/doc/openvpn/client1.key

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
ns-cert-type server

# If a tls-auth key is used on the server
# then every client must also have the key.
;tls-auth ta.key 1

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
;cipher x

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
;mute 20
root@raspberrypi:/home/pi#

```

Any tips advice commands or bandages for a sore head greatly received.

---

### Post by Irihapeti on 2016-12-21
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2016-12-21
What do you want to achieve, the Box to communicate to the office server using 192.168.1.6?

In such case, you need two things.
1. First the openvpn client (RPi) has to know to send the traffic for 192.168.1.0/24 over the tunnel. In server.conf add/use:
```
push "route 192.168.1.0 255.255.255.0"
```

Restart the openvpn service on the server after the changes to the config file.

2. Now the Box needs to know to send traffic for 192.168.1.0/24 to the RPi instead of its default router (the home router). Usually you would do that with static route:
```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 10.2.255.2
```

To make that permanent in /etc/network/interfaces on the Box for the ethernet interface add:
```
up route add -net 192.168.1.0/24 gw 10.2.255.2
```

That should keep it permanent over reboots.

---

### Post by jonobr on 2016-12-21
Hi Darkod!

Thanks for replying
I am trying to get "box" to register with the server. It sends a registration packet to the server and that should be all. 
I dont need to route to the subnet beyond that.
I do intend to have multiple vpns and other boxes, but im like a horse falling at the first fence.

I can ping 10.8.0.1 (the server side interface) and can ssh from the pi side, but would prefer to use the 192.168.1.6 address- however, right now I would be happy for each either interface

When I added the route you mentioned to the pi and to server.conf , i notice it uses eth0 interface on the pi, which I think is wrong. 

I decided to add 
route 192.168.1.0 255.255.255.0
to the server.conf as well and it populates correctly on the pi end which I think was the goal.
here is the pi route table now

```

root@raspberrypi:/home/pi# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
10.2.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.8.0.1        10.8.0.5        255.255.255.255 UGH       0 0          0 tun0
10.8.0.5        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     10.8.0.5        255.255.255.0   UG      


```

So that looks like what you mention , but I still cant seem to ssh or ping from box to server (10.8.0.1 or 192.168.1.6)

Thanks for your patience!





I added

---

### Post by darkod on 2016-12-21
You should not add 'route 192.168.1.0 255.255.255.0' to server.conf. If you read the instructions/comments in server.conf carefully you will see that you use that command for subnets that are behind the openvpn client, not behind the openvpn server like in your case. Please remove that command and use only the push route like I specified. Then reconnect the vpn and test if the RP can ping 192.168.1.6. That is what you need to make work first, the first step. Does it ping and ssh 192.168.1.6?

---

### Post by SeijiSensei on 2016-12-21
Did you enable packet forwarding in /etc/sysctl.conf?  If not, remove the hash mark from the beginning of the line that reads "net.ipv4.ip_forward=1" in that file and reboot.  Any better?

By default Ubuntu will not forward packets across interfaces for security reasons.

---

### Post by jonobr on 2016-12-21
SeijiSensei- I have been off the forums for a bit, great to see your still plugging away helping out people!

Yes I had ip forwarding on on the pi and the server.

Darknod

I found a couple of problems probably due to tiredness and sick of looking at this! Included were a faulty subnet for eth1 . I had a /18 instead of a /16

Anyway, I returned to your config

I can ping from box to pi, pi to 192.168.1.6 (YAY- Thanks !) but not box to 192.168.1.6
I assume I need a route on my Server back to box?


Here is my routing table on pi now 
```

pi@raspberrypi:~ $ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
10.2.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.8.0.1        10.8.0.5        255.255.255.255 UGH       0 0          0 tun0
10.8.0.5        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     10.8.0.5        255.255.255.0   UG        0 0          0 tun0
pi@raspberrypi:~ $
```


Also a pic of me on the Box and then sshing to the pi

[ATTACH=CONFIG]272804[/ATTACH]

---

### Post by darkod on 2016-12-21
OK, now you have the Pi able to use 192.168.1.6.

For the Box system, you need a route on it too unless it is already using the Pi as default gateway. So, on the Box machine please post the output of:
```
route -n
```

Then, you say you have enabled ipv4 forward in /etc/sysctl.conf on the Pi. But there is another step you need to make routing function. Even if you are not using iptables as firewall, you at minimum need a MASQUERADE rule. If you are using iptables to block traffic on the Pi you need more rules. But to start with, try the following on the Pi:
```
sudo iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
```

That allows traffic leaving the Pi over the vpn tunnel to be routed back correctly.

No, you wouldn't need any static route on the Server especially if Box is the one initiating the connection. Try the above first and let us know.

---

### Post by jonobr on 2016-12-21
Mmmmmmm..................


Iptables - Completely ignored that...... excellent point.
Let me take a look.

I greatly appreciate your help darknod! I have been working on linux for a long time and vpns were usually boxes with clicky GUIs,
let me get back to you!

---

### Post by jonobr on 2016-12-21
Thats awesome. I can ping the 192.168.1.6 from the box...
I am not registering but I think thats a lot closer, I appreciate your patience with me Darkod!
My regsitrations on 443 are not getting through but I think Ill put a wireshark on that.
Im also trying to get an SSH working from the openserver back to the box, but Ill wireshark that to.

Would that require more entries into iptables? 

Thanks so much!

---

### Post by darkod on 2016-12-21
If you want Server to communicate with 10.2.0.0/16 subnet, then more steps are needed.

1. In the server.conf add:
```
client-config-dir ccd
route 10.2.0.0 255.255.0.0
```

Create the folder /etc/openvpn/ccd.

2. Lets assume you created the client certificate as client1 (remember, you had to give it common name, you can see it in openvpn-status.log when the client is connected).
Inside the ccd folder create simple text file with name identical to the client common name (for example client1). Inside this file put just this line:
```
iroute 10.2.0.0 255.255.0.0
```

That's not a typo, it should start with an 'i'.

These two steps tell the setup how to route traffic for 10.2.0.0/16 over the vpn infra. Reconnect the server-client and try pinging the Box from Server, it should work.

---

### Post by jonobr on 2016-12-22
Darkod


This is awesome

I had that ccd config enabled before but it didn't seem to do anything and figured it was not what i needed.

I re-enabled and shazaam! It looks like its all working!

Thanks so much for your knowledge and help and your patience in dealing with me.

Cheers!

---

### Post by darkod on 2016-12-22
At that time it was probably not working because of the missing masquerade rule on the Pi. You want the Pi to act as linux router, and three basic rules are needed for linux to act as router:
1. If it's on internal subnets and no firewall is needed, do not block any traffic with iptables. Otherwise you will need specific rules to allow the traffic you need.
2. Enable forward in /etc/sysctl.conf
3. Set up iptables MASQUERADE rule.

Also don't forget that the masquerade rule on the Pi as I wrote it on the command line is temporary and doesn't survive a reboot. To survive a reboot you will need to use something like iptables-restore calling a file (usually you put a command in /etc/network/interfaces, ask if you need help with it), or because the masquerade command is only a single command it's much easier to simply put it in /etc/rc.local (above the exit 0 line) and it will be called at the end of each boot.

---

### Post by jonobr on 2016-12-22
Darkod, 

You are awesome. I really appreciate the follow up.

I knew the rule was temporary so its all good for my testing.

I think I had the solution already, but I thnk you are right, I was missing the IPtables rule to make it all work

I also assume that any other boxes placed beside the original box , connected to that segment need the same static route and they should work

Cheers again!

---

### Post by darkod on 2016-12-22
It depends... If the vpn client is the default GW for all boxes on that segment, then no static routes are needed. This is because the boxes will send all traffic to its GW anyway (in this case the vpn client), and because the vpn client knows how to route to 192.168.1.0/24 (the other side over the vpn tunnel), no specific routes will be needed.

If on the 10.2.0.0/16 subnets you have default GW different from the vpn client, then this GW doesn't know how to route to 192.168.1.0/24 correctly. You have two solutions:
1. A static route on the boxes which means they will be sending traffic destined for 192.168.1.0/24 to the vpn client instead of its default GW.
2. A static route on the default GW which will tell it to send traffic destined for 192.168.1.0/24 to the vpn client.

Depending how many boxes we are talking about, option 2 might be better. And if you can set static routes on the GW.

Otherwise you might need to set routes manually on a great number of boxes...

---

