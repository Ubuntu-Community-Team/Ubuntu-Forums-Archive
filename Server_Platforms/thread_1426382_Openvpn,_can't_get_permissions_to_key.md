---
title: "Openvpn, can't get permissions to key"
date: 2010-03-10
forum: Server Platforms
---

### Post by exutable on 2010-03-10
Hey guys,

Trying to set up a VPN on my seedbox. I get an error when I try to start it.

I followed this guide:  [http://www.ossramblings.com/configuring_openvpn_ubuntu_hardy]("http://www.ossramblings.com/configuring_openvpn_ubuntu_hardy")


Here is my server.conf:

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
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
;proto tcp
proto tcp

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
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh /etc/openvpn/keys/dh1024.pem

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
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
push "route 192.168.1.5 255.255.255.0"
push "route 192.168.1.128 255.255.255.0"

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
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway"

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
;max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
user nobody
group nobody

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

Here is the error I get when I run as normal user:
```
hd406-d2@ds8872:~$ openvpn /etc/openvpn/server.conf
Wed Mar 10 15:04:26 2010 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Wed Mar 10 15:04:26 2010 Cannot open /etc/openvpn/keys/dh1024.pem for DH parameters: error:0200100D:system library:fopen:Permission denied: error:2006D002:BIO routines:BIO_new_file:system lib
Wed Mar 10 15:04:26 2010 Exiting
hd406-d2@ds8872:~$ 
```

and as root:
```
root@ds8872:/home/hd406-d2# openvpn /etc/openvpn/server.conf
Wed Mar 10 15:05:29 2010 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Wed Mar 10 15:05:29 2010 Diffie-Hellman initialized with 1024 bit key
Wed Mar 10 15:05:29 2010 WARNING: file '/etc/openvpn/keys/server.key' is group or others accessible
Wed Mar 10 15:05:29 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Wed Mar 10 15:05:29 2010 TLS-Auth MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Wed Mar 10 15:05:29 2010 Note: Cannot open TUN/TAP dev /dev/net/tun: Operation not permitted (errno=1)
Wed Mar 10 15:05:29 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Wed Mar 10 15:05:29 2010 Cannot allocate TUN/TAP dev dynamically
Wed Mar 10 15:05:29 2010 Exiting
root@ds8872:/home/hd406-d2# 

```

---

### Post by exutable on 2010-03-10
oops, cant I get this moved to networking?

---

### Post by samosamo on 2010-03-10
You certainly can't run OpenVPN as a normal user.  Also I suggest using UDP, is there a reason why you are using TCP?

I quoted your problem below. It doesn't seem to be a problem with your keys.  Looks like a driver issue.  Can you please post the output of "lsmod | grep tun"

```
Wed Mar 10 15:05:29 2010 Note: Cannot open TUN/TAP dev /dev/net/tun: Operation not permitted (errno=1)
```

---

### Post by exutable on 2010-03-10
Hey samosamo,

In the guide he wrote that he had better success with tcp but it was on UDP default, so I'll go back to that.

Here is the output:
```
root@ds8872:/home/hd406-d2# lsmod | grep tun
root@ds8872:/home/hd406-d2# 

```

---

### Post by samosamo on 2010-03-10
Always use UDP.  Always.  Unless you can't, for example your network blocks it or something.  Then you use TCP.

Your tun driver isn't installed or not loading correctly. The guide you are using may be inadequate.  First try loading the module by doing "modprobe tun" and try again.  If the module fails to load post back here and we'll take another look.

---

### Post by exutable on 2010-03-10
Any reason for always using UDP?

Here is what I get:
```
root@ds8872:/home/hd406-d2# modprobe tun
FATAL: Could not load /lib/modules/2.6.27.42-vz-kvm-mod-0.5/modules.dep: No such file or directory
root@ds8872:/home/hd406-d2# 

```

---

### Post by samosamo on 2010-03-11
> **exutable said:**
> Any reason for always using UDP?

Here is what I get:
```
root@ds8872:/home/hd406-d2# modprobe tun
FATAL: Could not load /lib/modules/2.6.27.42-vz-kvm-mod-0.5/modules.dep: No such file or directory
root@ds8872:/home/hd406-d2# 

```

It is out of the scope of this thread but just know that UDP is a much more efficient protocol for handling OpenVPN traffic.

You're having a problem loading kernel modules. OpenVPN isn't really your problem after all. I'm sorry I can't help you any further.  You're using virtual machine software I'm just not familiar with.   Try the following:

Run "depmod -a" then try modprobe again.
Google terms like "ubuntu modules.dep: No such file or directory"
Make a thread in the ubuntu virtualization subforum

---

### Post by exutable on 2010-03-11
Well thank you Samosamo,

Here's what I get so I'll try figuring that out.


```
hd406-d2@ds8872:~$ depmod -a
WARNING: Couldn't open directory /lib/modules/2.6.27.42-vz-kvm-mod-0.5: No such file or directory
FATAL: Could not open /lib/modules/2.6.27.42-vz-kvm-mod-0.5/modules.dep.temp for writing: No such file or directory
hd406-d2@ds8872:~$ 
```

---

