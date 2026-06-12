---
title: "OpenVPN server, cannot start"
date: 2008-06-30
forum: Server Platforms
---

### Post by WintechAB on 2008-06-30
Hello. I am trying to install an OpenVPN-server on my machine. I have followed the how-to guid here: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

When i try to start the daemon ( sudo /etc/init.d/openvpn start ) it only says:
```
 * Starting virtual private network daemon.                                                                               sh: bridgeup.sh: not found
 * server (FAILED)
                                                                                                                   [ OK ]
```

And in the log file i find this:
```
Jun 30 10:31:08 brasse ovpn-server[753]: OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Jun 30 10:31:08 brasse ovpn-server[753]: PLUGIN_INIT: POST /usr/lib/openvpn/openvpn-down-root.so '[/usr/lib/openvpn/openvpn-down-root.so] [bridgedown.sh]' intercepted=PLUGIN_UP|PLUGIN_DOWN 
Jun 30 10:31:08 brasse ovpn-server[753]: Diffie-Hellman initialized with 1024 bit key
Jun 30 10:31:08 brasse ovpn-server[753]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Jun 30 10:31:09 brasse ovpn-server[753]: Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Jun 30 10:31:09 brasse ovpn-server[753]: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Jun 30 10:31:09 brasse ovpn-server[753]: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Jun 30 10:31:09 brasse ovpn-server[753]: TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Jun 30 10:31:09 brasse ovpn-server[753]: TUN/TAP device tap0 opened
Jun 30 10:31:09 brasse ovpn-server[753]: TUN/TAP TX queue length set to 100
Jun 30 10:31:09 brasse ovpn-server[753]: PLUGIN_CALL: POST /usr/lib/openvpn/openvpn-down-root.so/PLUGIN_UP status=0
Jun 30 10:31:09 brasse ovpn-server[753]: bridgeup.sh tap0 1500 1574   init
Jun 30 10:31:09 brasse ovpn-server[753]: script failed: could not execute shell command
Jun 30 10:31:09 brasse ovpn-server[753]: Exiting
```

Can anyone help me?

Edit, my server.conf:

```
mode server
tls-server

# ip/hostname of server
local brasse.se
# default openvpn port
port 1194
proto udp



# bridging directive
# name of tap device to create
dev tap0
up bridgeup.sh
up-restart
plugin /usr/lib/openvpn/openvpn-down-root.so "bridgedown.sh"

persist-key
persist-tun
# allow the clients to communicate amongst themselves
client-to-client
up bridgeup.sh

#certificates and encryption
ca ca.crt
cert server.crt
# This file should be kept secret
key server.key
dh dh1024.pem
# This file is secret
tls-auth ta.key 0
# Blowfish (default)
cipher BF-CBC
comp-lzo

# DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.23.1 255.255.255.0 192.168.23.100 192.168.23.149
push "dhcp-option DNS 192.168.23.1"
push "dhcp-option DOMAIN vlab"
push "route 192.168.23.0 255.255.255.0"
# set this to the max number of clients that should be connected at a time
max-clients 10

#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3
```

---

### Post by claytronic on 2008-09-16
It looks like your bridgeup.sh script doesn't have execute permissions under the "nobody" account.

---

