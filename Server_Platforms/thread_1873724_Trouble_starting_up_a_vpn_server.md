---
title: "Trouble starting up a vpn server?"
date: 2011-11-01
forum: Server Platforms
---

### Post by sirspazzolot on 2011-11-01
```
matt@matt:/etc/openvpn/easy-rsa$ sudo openvpn /etc/openvpn/server.conf
Tue Nov  1 20:23:51 2011 OpenVPN 2.1.3 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Mar 11 2011
Tue Nov  1 20:23:51 2011 NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Tue Nov  1 20:23:51 2011 NOTE: your local LAN uses the extremely common subnet address 192.168.0.x or 192.168.1.x.  Be aware that this might create routing conflicts if you connect to the VPN server from public locations such as internet cafes that use the same subnet.
Tue Nov  1 20:23:51 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Tue Nov  1 20:23:51 2011 Cannot open /etc/openvpn/keys/dh1024.pem for DH parameters: error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file

```
that's what I get from running
```
sudo openvpn /etc/openvpn/server.conf
```

Am I supposed to run the openvpn command with that --script-security 2 thing or is that supposed to be input somewhere in the config file? I followed the setup instructions [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/C/openvpn.html").
The server fails to start and it gives the message above. /etc/openvpn/keys/dh1024.pem does in fact exist. I may change my local subnet to something less common later. Not totally sure what the bridging/TAP one is about, but ifconfig says the address of the br0 interface is the same as eth0. Would I be able to connect to the vpn from the same network it's on for testing purposes, or since the subnet address is technically the same, is it impossible?

I'll post the contents of server.conf, minus anything that was commented out.

```
local 192.168.1.104

port 25252

proto udp

dev tap0

ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret

dh /etc/openvpn/keys/dh1024.pem

up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

ifconfig-pool-persist ipp.txt

server-bridge 192.168.1.104 255.255.255.0 192.168.1.50 192.168.1.100

push "route 192.168.1.100 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"

push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"

keepalive 10 120

tls-auth /etc/openvpn/keys/ta.key 0 # This file is secret

cipher DES-EDE3-CBC  # Triple-DES
comp-lzo

user nobody
group nogroup

persist-key
persist-tun

status /var/log/openvpn-status.log

verb 3

crl-verify /etc/openvpn/easy-rsa/2.0/keys/crl.pem

```

Thanks in advance! Let me know if I'm getting in over my head. I'm on Ubuntu Server 11.10.

---

### Post by sirspazzolot on 2011-11-02
I'm using OpenVPN, by the way. pptpd supposedly does not work on my router. I don't remember the exact model number of it.

---

### Post by sirspazzolot on 2011-11-12
Okay, so I redid the config file and blah blah pretending to know what I'm doing. now here's where I am. I run ```
 sudo openvpn --mode server --dev tap0 --tls-server --dh dh1024.pem --ca ca.crt --cert server.crt --script-security 2 --key ta.key server.conf

```
and get ```
blah blah blah
Sat Nov 12 01:27:01 2011 Cannot load private key file ta.key: error:0906D06C:PEM routines:PEM_read_bio:no start line: error:140B0009:SSL routines:SSL_CTX_use_PrivateKey_file:PEM lib
Sat Nov 12 01:27:01 2011 Error: private key password verification failed
Sat Nov 12 01:27:01 2011 Exiting

```

I used my 1337 h4x0r skills and opened it up in nano and it's
```

#
# 2048 bit OpenVPN static key
#
-----BEGIN OpenVPN Static key V1-----
LOL NUMBERS AND STUFF
-----END OpenVPN Static key V1-----

```

It most certainly has a start line. After some googling I found [[COLOR="RoyalBlue"]this[/COLOR]]("http://is.gd/s5dJq2") which says it's encoded in UTF-8 instead of ANSI which is bad or something. I don't know what to do from here. Is there a way to re-encode my ta.key? I apologize for the name of the site I linked to, by the way... At the very least, the page I linked to is SFW if you overlook the bad word in the name.

Halp plawks

---

### Post by sirspazzolot on 2011-11-13
Could I just straight up bypass the part of openvpn that requires ta.key? (tls-auth)

it still asks me to specify --key after commenting out the line related to it in the config file.

---

### Post by SeijiSensei on 2011-11-14
If you're just setting up a point-to-point tunnel, using a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") is a lot easier than public-key methods.

---

