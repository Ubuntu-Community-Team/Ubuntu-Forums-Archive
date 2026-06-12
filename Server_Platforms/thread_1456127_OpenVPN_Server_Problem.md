---
title: "OpenVPN Server Problem"
date: 2010-04-16
forum: Server Platforms
---

### Post by cian1500ww on 2010-04-16
I've been looking into setting up a VPN server on a dedicated box that I'm renting. I've been following the guide on Ubuntu's website for Ubuntu Server 9.10 but I keep getting a fail error when starting up OpenVPN.
```
root@ks311063:/etc/openvpn/easy-rsa/2.0# sudo sudo /etc/init.d/openvpn restart
 * Stopping virtual private network daemon(s)...                                                                                                              *   No VPN is running.
 * Starting virtual private network daemon(s)...                                                                                                              *   Autostarting VPN 'client' 
```

Here is my server.conf file:
```

#################################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
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
local 188.165.205.255

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
;proto tcp
proto udp

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
dev tap0

# Windows needs the TAP-Win32 adapter name
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
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

# Maintain a record of client <-> virtual IP address
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
server-bridge 188.165.205.255 255.255.255.0 188.165.205.255 188.165.205.265

# Configure server mode for ethernet bridging
# using a DHCP-proxy, where clients talk
# to the OpenVPN server-side DHCP server
# to receive their IP address allocation
# and DNS server addresses.  You must first use
# your OS's bridging capability to bridge the TAP
# interface with the ethernet NIC interface.
# Note: this mode only works on clients (such as
# Windows), where the client-side TAP adapter is
# bound to a DHCP client.
;server-bridge

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
push "route 188.165.205.255 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"

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
;route 192.168.40.128 255.255.255.248
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
# or bridge the TUN/TAP interface to the internet
# in order for this to work properly).
;push "redirect-gateway def1 bypass-dhcp"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
# The addresses below refer to the public
# DNS servers provided by opendns.com.
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"

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
tls-auth ta.key 0 # This file is secret

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
;max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
user nobody
group nogroup

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
```

And my client config file:
```

###############################################
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
dev tap

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
;proto tcp
proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote new 1194
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
;mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca ca.crt
cert new.crt
key new.key

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
tls-auth ta.key 1

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
```

And here's the output of ifconfig:
```
root@ks311063:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:f8:40:be
          inet addr:188.165.205.19  Bcast:188.165.205.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:374303326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638549714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:166254615712 (166.2 GB)  TX bytes:858839629282 (858.8 GB)
          Memory:faee0000-faf00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7111332 (7.1 MB)  TX bytes:7111332 (7.1 MB)

```

Any help would be much appreciated !!

---

### Post by gombadi on 2010-04-16
In your server config

> 
# Which local IP address should OpenVPN
# listen on? (optional)
local 188.165.205.255


That is the broadcast address for your servers network - you want to use 188.165.205.19

and in your client config
> 
# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote new 1194


Unless you have a dns entry pointing new to 118.165.205.19 then this will not work.

Also have a look at /var/log/syslog. It contains a lot of useful information and any errors from OpenVPN.

---

### Post by cian1500ww on 2010-04-16
> **gombadi said:**
> In your server config



That is the broadcast address for your servers network - you want to use 188.165.205.19

and in your client config


Unless you have a dns entry pointing new to 118.165.205.19 then this will not work.

Also have a look at /var/log/syslog. It contains a lot of useful information and any errors from OpenVPN.
Thanks for your help, I've modified the files. Still failing to start though. Heres whats in the log from openvpn:
```
Apr 17 01:02:24 stock ovpn-client[29599]: OpenVPN 2.1_rc19 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Apr 17 01:02:24 stock ovpn-client[29599]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Apr 17 01:02:24 stock ovpn-client[29599]: Cannot load certificate file new.crt: error:02001002:system library:fopen:No such file or directory: error:2007400$
Apr 17 01:02:24 stock ovpn-client[29599]: Exiting

```

---

### Post by gombadi on 2010-04-17
> 
Cannot load certificate file new.crt: error:02001002:system library:fopen:No such file or directory: error:2007400$


If you look in the client config file you will see a reference to new.crt. 

> 
# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca ca.crt
cert new.crt
key new.key


Where is that file? May pay to make the reference in the config file to an absolute path like /etc/openvpn/keys/new.crt so you and the software know exactly what file you are talking about.

---

### Post by cian1500ww on 2010-04-17
> **gombadi said:**
> If you look in the client config file you will see a reference to new.crt. 



Where is that file? May pay to make the reference in the config file to an absolute path like /etc/openvpn/keys/new.crt so you and the software know exactly what file you are talking about.
Yep, thanks mate, that solved the problem. It's starting the VPN server fine now but I can't seem to connect, I keep getting a TCP error ?? Any ideas:
```
Sat Apr 17 14:10:52 2010 OpenVPN 2.1.1 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Dec 11 2009
Sat Apr 17 14:10:52 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Apr 17 14:10:52 2010 LZO compression initialized
Sat Apr 17 14:10:52 2010 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Sat Apr 17 14:10:52 2010 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Sat Apr 17 14:10:52 2010 Local Options hash (VER=V4): '69109d17'
Sat Apr 17 14:10:52 2010 Expected Remote Options hash (VER=V4): 'c0103fa8'
Sat Apr 17 14:10:52 2010 Attempting to establish TCP connection with 118.165.205.19:1194
Sat Apr 17 14:11:13 2010 TCP: connect to 118.165.205.19:1194 failed, will try again in 5 seconds: Connection timed out (WSAETIMEDOUT)
Sat Apr 17 14:11:39 2010 TCP: connect to 118.165.205.19:1194 failed, will try again in 5 seconds: Connection timed out (WSAETIMEDOUT)

```

---

### Post by spynappels on 2010-04-17
I'm not sure why, but it is trying to connect on TCP rather than UDP. Your Client file states to use UDP, so it check that this has not been changed accidentally to TCP between when it was posted above and now.

---

### Post by cian1500ww on 2010-04-17
> **spynappels said:**
> I'm not sure why, but it is trying to connect on TCP rather than UDP. Your Client file states to use UDP, so it check that this has not been changed accidentally to TCP between when it was posted above and now.
Apologies, I should have explained that I switched it to UDP to stop a TLS error that was happening when I was connecting.

---

### Post by spynappels on 2010-04-18
Ok, now I'm a little confused. Are you running the service on TCP or on UDP?

UDP is the normal one to listen on, I tend to use TCP only when some specific firewalls cause problems for UDP traffic.

If it is TCP (or UDP for that matter), you need to check that you can connect using the LAN IP, so make a new client.conf file specifying your LAN IP rather than "new" and see if it will allow you to connect across the LAN. The reason is that some routers/gateways will not allow you to use the Public IP from inside the LAN. Also, check that port forwarding is enabled and that port 1194 UDP or TCP has been forwarded to your OpenVPN server.

If you have already done all this, we'll have to look at different causes of the problem.

Oh, just to add, if you want to check whether a config works, in the openvpn directory run the following:

```
sudo openvpn --config client.conf
```

substituting the name of your client file. This will allow you to see the output of the command. If all works correctly, kill the process with Ctrl+C and then run it using the ```
sudo /etc/init.d/openvpn start
``` command.

---

