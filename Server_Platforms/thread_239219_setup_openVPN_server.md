---
title: "setup openVPN server?"
date: 2006-08-18
forum: Server Platforms
---

### Post by kpham.p on 2006-08-18
Hello all,

I've been following some of the document on openvpn.net. and still can't configure it to work on ubuntu server.

I install openVPN via Synaptic.  is there away to configure it to work in ubuntu server?

thanks,
Kpham.p

---

### Post by bunnynuts on 2006-08-20
I may be able to help...I have recently set up a couple routed openVPN servers...I'm new to it and had difficulties...and others may better help, but let me know what you want to do with it and how far you have gotten and I'll see if I can help

---

### Post by tonym on 2006-08-21
What do you want to do with it?

---

### Post by kpham.p on 2006-08-21
Thank you all for replying to my thread.

Well, I have an old machine and I'd like to use this machine to be my personal vpn server.  basically I'd want to connect to my network from outside of my house (i.e @work, friend's house, hotel...etc) so then I can use this connection to remote on other local machine on the network.  mainly I like to be able to connect to my home network and control all of the machine via terminal or realVNC.

thanks all
Kpham.p

---

### Post by bunnynuts on 2006-08-22
You are going to want to set up a bridged vpn server, something I've never done.  However, I can walk you through the steps to set up the server/client keys if you would like. Mine is routed and I only use it to access files via a samba share.  Unless I'm mistaken the differentiation between routed and bridged server is in the server/client config files...so lets get you there and hopefully someone else can add to this, or we can struggle through it. 
Additionally, I only did the basic server installation so I'm working from command line only.

Most of the posts available in the forums advise people to follow the How-To on the openvpn.net site.  I agree but will try to make it a bit more simple.  I hope I'm not wasting your time with the simplicity of my instructions. Also, I'm assuming you are vaguely familiar with vi. If not use gedit or whatever you like.  Also here is a nice concise vi guide:

[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

First you need to install openvpn and openssl to do so from the command line:

```
sudo apt-get install openvpn
```

and 

```
sudo apt-get install openssl
```

Next you need to change directories to the easy-rsa directory:

```
cd /etc/openvpn/easy-rsa
```

If there are no subdirectories in the openvpn directory copy the easy-rsa directory from /usr/share/doc/openvpn/examples/easy-rsa to the /etc/openvpn directory

First go to the examples directory 

```
cd /usr/share/doc/openvpn/examples
```

Then copy the easy-rsa directory to the /etc/openvpn location

```
sudo cp -r easy-rsa /etc/openvpn
```

You should now edit the vars file located in this newly created easy-rsa directory: 

```
sudo vi vars
```

Change the fields mentioned in the openvpn.net site. Next, while in the easy-rsa directory enter the following:

```
. ./vars
```

Note the space between the periods. Next enter:

```
sudo ./clean-all
```

Then enter:

```
sudo ./build-ca
```

Note that when you do this you must enter something for the "common name." 

Now enter the following inserting your server's name:

```
sudo ./build-key-server *yourserver's name here*
```

When it asks for the common name enter your server's name. Next build your client key (again while in the easy-rsa directory).

```
sudo ./build-key *client name here*
```

If you want the server to prompt you for a password before you can connect to the vpn server enter:

```
sudo ./build-key-pass *client name here*
```

Repeat the step you used to create the client key for the number of keys you want to create, chagning the client name for each

Now you build the Diffie Hellman parameters:

```
sudo ./build-dh
```

All the server keys and client keys are in the keys directory which is in the easy-rsa directory.  You will need to be root to gain access to the keys directory:

```
sudo su
```

Copy the client keys: ca.crt, client.key, client.csr, client.crt to the client computer.  You will always have a ca.crt file, the client files will be named whatever name you gave the client.  

You now need to create the server configuration file.  To do this (I doubt it is the best way but it worked) I copy/pasted the sample server config file from the openvpn.net site into a newly created file named server.conf inside the /etc/openvpn directory. 

```
sudo vi /etc/openvpn/server.conf
```

This will open an empty file, you can then paste the copied sample server.conf into it.  

From here you need to edit the server.conf file for a bridged server...which I haven't ever done. 

For the initial start of the daemon do the following while in the directory containing your server config file:

```
openvpn --daemon --config configfilenamehere
```

If this was helpful and you want/need help with setting things up on the client side let me know.  
If there is anything that is unclear please let me know. If I get some time I'll look up things for the bridged server part and see if I can offer any further help.  Additionally, here are a few websites that may offer help:
[http://mia.ece.uic.edu/~papers/volans/openvpn1.html](http://mia.ece.uic.edu/~papers/volans/openvpn1.html)
[http://deb.riseup.net/networking/openvpn/](http://deb.riseup.net/networking/openvpn/)
[http://www.batcom-it.net/index.php?option=com_content&task=view&id=32&Itemid=41](http://www.batcom-it.net/index.php?option=com_content&task=view&id=32&Itemid=41)
[http://gentoo-wiki.com/HOWTO_OpenVPN_Server_for_Ethernet_Bridging_with_Server_Certificates](http://gentoo-wiki.com/HOWTO_OpenVPN_Server_for_Ethernet_Bridging_with_Server_Certificates)
[http://www.skippy.net/trac/wiki/OpenVPN](http://www.skippy.net/trac/wiki/OpenVPN)
[http://www.packtpub.com/page/OpenVPN:_Building_and_Integrating_Virtual_Private_Networks_Table_of_Contents](http://www.packtpub.com/page/OpenVPN:_Building_and_Integrating_Virtual_Private_Networks_Table_of_Contents)

---

### Post by bunnynuts on 2006-08-22
I've decided to include a sample server.conf file. Again it is a routed vpn server so yours will be different.  Also I left my keys in the keys subdirectory as opposed to moving them to the same directory where the server.conf file is located thus the whole path to the key files in the file. To repeat, probably not the best way but it works :). This is from openvpn.net.

```
###########################################
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
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/servername.crt
key /etc/openvpn/easy-rsa/keys/server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh /etc/openvpn/easy-rsa/keys/dh1024.pem

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
;push "route 192.168.10.0 255.255.255.0"
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
# [http://openvpn.net/faq.html#dhcpcaveats](http://openvpn.net/faq.html#dhcpcaveats)
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

---

### Post by Useless on 2006-08-22
I have a cheap and easy way to do this....simply using ssh.  If you set up openSSH you can ssh in to your own box and while in that session, ssh in to another box on your network.  You can set it up to tunnel traffic as well, by tunneling your browser back in to a loop back address and be able to browse anything with a web service on  your local network.  

I have an ubuntu box which i SSH in to and use to be able to connect to any of my machines at home and grab some files as well as use as an encrypted tunnel for when i am on a public wifi hotspot for extra security.  

If interested in setting this up, let me know.  Its fairly simple and if you have a good passkey, very secure.

---

### Post by bunnynuts on 2006-08-22
Useless,

I can not speak for the person who started the thread, but I would be interested.  Probably not nice to jack his/her thread so if you started a new one (unless he/she is also interested) I would appreciate it :). Thanks.

---

### Post by terigox on 2006-08-22
Bunny: I like this how-to and will be trying it soon! I've been looking for a way to do this for a while, but haven't really had much success, so thanks! I hope it works :)

---

### Post by bunnynuts on 2006-08-22
No problem, just be sure that you follow along with the openvpn.net How-To in order to get the most of it.  Additionally, if you plan on using a routed openvpn server you will need to install/configure a WINS server such as samba. Let me know if you have any questions.

---

### Post by kpham.p on 2006-08-22
Awesome guys....

lately I didn't have time to check to forums :) cause of baby lol.  anyway, I will try bunnynuts' method on setting up my first openVPN server and let ya'll know how it goes.

about SSH tunneling -- I would love to learn about it.  Its always beneficial to learn something new.

thanks guy.

Kpham.p

---

### Post by keronas on 2006-11-27
i had a problem with the variants on the vars file
try this :confused: 
# source ./vars
i now it is off date but i put here because this thread has a complete guide how to   set up openvpn  :mrgreen: tnx

---

### Post by SBFC on 2007-04-08
I don't mean to create a zombie thread here, but I had a question regarding bunnynuts very useful instructions.

> Now you build the Diffie Hellman parameters:

Code:

sudo ./build-dh



What does this step do exactly? Or rather, what does building the Diffie Hellman parameters do? Is this step only required once? If I create a bunch of keys now, and then a few weeks from now create a few more, am I supposed to do this step again?

Thanks.

---

