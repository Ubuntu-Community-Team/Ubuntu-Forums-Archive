---
title: "Anyone good with OpenVPN AS config?"
date: 2017-04-09
forum: Server Platforms
---

### Post by dev18 on 2017-04-09
Greetings,
    So I have a Ubuntu 16.04 VPS I'm attempting to run OpenVPN Access Server to make my own VPN service. I've had hit and miss when it comes to success. Over the past couple of days, I've followed the many tutorials out there. Some are short and some are very long. But in the end, my .ovpn configuration files never work. I always end up having to rebuild the VPS to try again after digging myself into a hole that I don't understand. :) 


   I use Linux, Android, and Windows. With Windows, I can go to https://<server_ip>:943 and browser connect and the "OpenVPN Connect" client to use the VPN. My public IP is changed and speeds are great! Though if I try the usual OpenVPN client with my .ovpn, it doesn't allow internet access. Linux, .ovpn is the only option, so no success there at all. 


   I'm not sure what the issue is exactly. While connected using the .ovpn, I can ping google via the IP, but not the DNS name (google.com). Any suggestions? 

```

dev@DESKTOP2:~/Documents/SMS$ sudo openvpn --config ~/Downloads/client2.ovpn 
Sun Apr  9 00:29:48 2017 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Feb  2 2016
Sun Apr  9 00:29:48 2017 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Enter Auth Username: ***
Enter Auth Password: ***************
Sun Apr  9 00:30:00 2017 Control Channel Authentication: tls-auth using INLINE static key file
Sun Apr  9 00:30:00 2017 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Apr  9 00:30:00 2017 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Apr  9 00:30:00 2017 Socket Buffers: R=[212992->200000] S=[212992->200000]
Sun Apr  9 00:30:00 2017 UDPv4 link local: [undef]
Sun Apr  9 00:30:00 2017 UDPv4 link remote: [AF_INET]<server_ip>:1194
Sun Apr  9 00:30:00 2017 TLS: Initial packet from [AF_INET]<server_ip>:1194, sid=<removed>
Sun Apr  9 00:30:00 2017 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sun Apr  9 00:30:00 2017 VERIFY OK: depth=1, CN=OpenVPN CA
Sun Apr  9 00:30:00 2017 VERIFY OK: nsCertType=SERVER
Sun Apr  9 00:30:00 2017 VERIFY OK: depth=0, CN=OpenVPN Server
Sun Apr  9 00:30:00 2017 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Apr  9 00:30:00 2017 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Apr  9 00:30:00 2017 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Apr  9 00:30:00 2017 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Apr  9 00:30:00 2017 Control Channel: TLSv1, cipher TLSv1/SSLv3 ECDHE-RSA-AES256-SHA, 2048 bit RSA
Sun Apr  9 00:30:00 2017 [OpenVPN Server] Peer Connection Initiated with [AF_INET]<server_ip>:1194
Sun Apr  9 00:30:03 2017 SENT CONTROL [OpenVPN Server]: 'PUSH_REQUEST' (status=1)
Sun Apr  9 00:30:03 2017 PUSH: Received control message: 'PUSH_REPLY,explicit-exit-notify,topology subnet,route-delay 5 30,dhcp-pre-release,dhcp-renew,dhcp-release,route-metric 101,ping 12,ping-restart 50,auth-token SESS_ID,comp-lzo yes,redirect-gateway def1,redirect-gateway bypass-dhcp,redirect-gateway autolocal,route-gateway 172.27.232.1,dhcp-option DNS 8.8.8.8,dhcp-option DNS 208.67.222.222,register-dns,block-ipv6,ifconfig 172.27.232.6 255.255.248.0'
Sun Apr  9 00:30:03 2017 Option 'explicit-exit-notify' in [PUSH-OPTIONS]:1 is ignored by previous <connection> blocks 
Sun Apr  9 00:30:03 2017 Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:4: dhcp-pre-release (2.3.10)
Sun Apr  9 00:30:03 2017 Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:5: dhcp-renew (2.3.10)
Sun Apr  9 00:30:03 2017 Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:6: dhcp-release (2.3.10)
Sun Apr  9 00:30:03 2017 Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:18: register-dns (2.3.10)
Sun Apr  9 00:30:03 2017 Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:19: block-ipv6 (2.3.10)
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: timers and/or timeouts modified
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: explicit notify parm(s) modified
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: LZO parms modified
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: --ifconfig/up options modified
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: route options modified
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: route-related options modified
Sun Apr  9 00:30:03 2017 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Apr  9 00:30:03 2017 ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=enp2s0 HWADDR=d8:cb:8a:33:22:dc
Sun Apr  9 00:30:03 2017 TUN/TAP device tun0 opened
Sun Apr  9 00:30:03 2017 TUN/TAP TX queue length set to 100
Sun Apr  9 00:30:03 2017 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Sun Apr  9 00:30:03 2017 /sbin/ip link set dev tun0 up mtu 1500
Sun Apr  9 00:30:03 2017 /sbin/ip addr add dev tun0 172.27.232.6/21 broadcast 172.27.239.255
Sun Apr  9 00:30:08 2017 ROUTE remote_host is NOT LOCAL
Sun Apr  9 00:30:08 2017 /sbin/ip route add <server_ip>/32 via 192.168.1.1
Sun Apr  9 00:30:08 2017 /sbin/ip route add 0.0.0.0/1 via 172.27.232.1
Sun Apr  9 00:30:08 2017 /sbin/ip route add 128.0.0.0/1 via 172.27.232.1
Sun Apr  9 00:30:08 2017 Initialization Sequence Completed
#
#Ctrl+C
#
^CSun Apr  9 00:32:28 2017 event_wait : Interrupted system call (code=4)
Sun Apr  9 00:32:28 2017 SIGTERM received, sending exit notification to peer
Sun Apr  9 00:32:29 2017 /sbin/ip route del <server_ip>/32
Sun Apr  9 00:32:29 2017 /sbin/ip route del 0.0.0.0/1
Sun Apr  9 00:32:29 2017 /sbin/ip route del 128.0.0.0/1
Sun Apr  9 00:32:29 2017 Closing TUN/TAP interface
Sun Apr  9 00:32:29 2017 /sbin/ip addr del dev tun0 172.27.232.6/21
Sun Apr  9 00:32:29 2017 SIGTERM[soft,exit-with-notification] received, process exiting

```

---

### Post by wildmanne39 on 2017-04-09
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-04-09
I haven't done any OpenVPN AS installations but I have installed quite a few openvpn servers (directly on ubuntu, not sure if AS installation is different). And clients have been able to connect from android, iOS, windows, linux...

Is your problem only with connecting linux clients? Post the client config file in CODE tags so we can have a look. Also, note that .ovpn is actually a windows extension, in linux usually people use .conf although any extension will work in linux. If it is .conf and if it is in /etc/openvpn then the connection will be started on boot. Otherwise you have to do it manually.

---

### Post by dev18 on 2017-04-09
> **darkod said:**
> I haven't done any OpenVPN AS installations but I have installed quite a few openvpn servers (directly on ubuntu, not sure if AS installation is different). And clients have been able to connect from android, iOS, windows, linux...

Is your problem only with connecting linux clients? Post the client config file in CODE tags so we can have a look. Also, note that .ovpn is actually a windows extension, in linux usually people use .conf although any extension will work in linux. If it is .conf and if it is in /etc/openvpn then the connection will be started on boot. Otherwise you have to do it manually.

No, its just there are just more options for connecting Windows clients. I've had no luck when using the configuration file for any operating system.
[CENTER][CENTER]

[/CENTER]
[LEFT]The image below is taken from **Windows**. You can click the link and get an "OpenVPN Connect" client. This client does NOT allow .ovpn configuration files. Its parameters are static-like. I can successfully connect to the VPN using that application. All that states is the server is somewhat functional.[/LEFT]
[IMG]http://i.imgur.com/zsxoN4w.jpg[/IMG]
[LEFT]The image below is taken from **Linux**. You do not have the connect option. So the only option is to use the configuration file (.ovpn extension on Windows).[/LEFT]

[IMG]http://i.imgur.com/DBUANrS.png[/IMG]
The "OpenVPN for Linux" redirects to here:
[https://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html](https://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html)[LEFT]
_________________________________________________[/LEFT]
[/CENTER]

Currently, the server is running whatever this package ([https://openvpn.net/index.php/access-server/download-openvpn-as-sw/113.html?osfamily=Ubuntu](https://openvpn.net/index.php/access-server/download-openvpn-as-sw/113.html?osfamily=Ubuntu) (dpkg -i <package>)) has installed and configured. (x64 bit)


Of course I tried other methods like [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04) . Which is obviously way different than simply installing a package. Using this tutorial took a long time and was completely unsuccessful.

_________________________________________________

As requested, the config file from the "Yourself" link in the image above. This deb installation doesn't not currently have a /etc/openvpn/server.conf file.

```

# Automatically generated OpenVPN client config file
# Generated on Sun Apr  9 00:17:30 2017 by vpn01
# Note: this config file contains inline private keys
#       and therefore should be kept confidential!
# Note: this configuration is user-locked to the username below
# OVPN_ACCESS_SERVER_USERNAME=openvpn
# Define the profile name of this particular configuration file
# OVPN_ACCESS_SERVER_PROFILE=openvpn@<serverip>
# OVPN_ACCESS_SERVER_CLI_PREF_ALLOW_WEB_IMPORT=True
# OVPN_ACCESS_SERVER_CLI_PREF_ENABLE_CONNECT=True
# OVPN_ACCESS_SERVER_CLI_PREF_ENABLE_XD_PROXY=True
# OVPN_ACCESS_SERVER_WSHOST=<serverip>:443
# OVPN_ACCESS_SERVER_WEB_CA_BUNDLE_START
# -----BEGIN CERTIFICATE-----
# MIIC/DCCAeSgAwIBAgIEWOm1YjANBgkqhkiG9w0BAQsFADA3MTUwMwYDVQQDDCxP
<removed>
# zn+lmGqKeKgfaKNiJIjzpO/tT0l+cioX0OgJtCtlncsP9G6gCDWuNvcmRqR/XucE
# 0ceGMQSB2NW93eLDv4u9gfWrt0FzFDG3IX1EhFlG1BIpKBPcvRPrJRytvsVYdTpc
# -----END CERTIFICATE-----
# OVPN_ACCESS_SERVER_WEB_CA_BUNDLE_STOP
# OVPN_ACCESS_SERVER_IS_OPENVPN_WEB_CA=1
# OVPN_ACCESS_SERVER_ORGANIZATION=OpenVPN Technologies, Inc.
setenv FORWARD_COMPATIBLE 1
client
server-poll-timeout 4
nobind
remote <serverip>1194 udp
remote <serverip>1194 udp
remote <serverip>443 tcp
remote <serverip>1194 udp
remote <serverip>1194 udp
remote <serverip>1194 udp
remote <serverip>1194 udp
remote <serverip>1194 udp
dev tun
dev-type tun
ns-cert-type server
reneg-sec 604800
sndbuf 100000
rcvbuf 100000
auth-user-pass
# NOTE: LZO commands are pushed by the Access Server at connect time.
# NOTE: The below line doesn't disable LZO.
comp-lzo no
verb 3
setenv PUSH_PEER_INFO


<ca>
-----BEGIN CERTIFICATE-----
MIICuDCCAaCgAwIBAgIEWOm1XTANBgkqhkiG9w0BAQsFADAVMRMwEQYDVQQDDApP
<removed>
cS4n2eb6n2v3IYPu8TUWud4E/0h/rjjAKzOeeQ==
-----END CERTIFICATE-----
</ca>


<cert>
-----BEGIN CERTIFICATE-----
MIICwjCCAaqgAwIBAgIBAjANBgkqhkiG9w0BAQsFADAVMRMwEQYDVQQDDApPcGVu
VlBOIENBMB4XDTE3MDQwMjA0MTcyM1oXDTI3MDQwNzA0MTcyM1owEjEQMA4GA1UE
<removed>
o6pt9QFRLy8592MS9iAOyqidjzl7XXcxYnaTJRcmscXwAhVmOBi1qKxC4cwM0TDC
gyKVMbkN5F6T5EiNgcH09EXPU1qA4V+QeZPVcKxCsmZK2yc53tg=
-----END CERTIFICATE-----
</cert>


<key>
-----BEGIN PRIVATE KEY-----
MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDX9S8a/sMdVrj4
Kad+2ybz5VaQRxtf9OttV2MyVehQ6DEF8JE5HQSlSdU+qEa7RRGq9eTy9OcWi0+m
<removed>
RZSC+9tUwc8l4VBnHy6MOxTIWSpc5XsiGJblhFjFDlFQDTNqcD6BjfrGQsYRvgk/
D2rC7pKf/x2ZtyLEGOVhDIs=
-----END PRIVATE KEY-----
</key>


key-direction 1
<tls-auth>
#
# 2048 bit OpenVPN static key (Server Agent)
#
-----BEGIN OpenVPN Static key V1-----
f948183ae4188875a99a26e38332244e
c72c91e23d576ce11d6232fbf898341e
<removed>
70f302fc436d01be8d34eb56428fbec5
-----END OpenVPN Static key V1-----
</tls-auth>


## -----BEGIN RSA SIGNATURE-----
## DIGEST:sha256
## DJOnT/j/SeW5i/WUI3M/s6O7P3xseTxd1Tu/Wj82yJxSHk8agF
<removed>
## ZsS6cddon0djjQhLXuyXn+tID1P+FTSMA/8UDfkDlA==
## -----END RSA SIGNATURE-----
## -----BEGIN CERTIFICATE-----
## MIIC5TCCAc2gAwIBAgIEWOm1YzANBgkqhkiG9w0BAQsFADA3MTUwMwYDVQQDDCxP
<removed>
## lRj4mqtM/101+hNe2Rzo2W9bxRpxs3IqM0Q2G+Tz5OLMB0wnEs0sFFRwWd+MRee2
## hnIWJF1BcoJL5jWlVu6H42Oy6fWDrUJupw==
## -----END CERTIFICATE-----
## -----BEGIN CERTIFICATE-----
## MIIC/DCCAeSgAwIBAgIEWOm1YjANBgkqhkiG9w0BAQsFADA3MTUwMwYDVQQDDCxP
## cGVuVlBOIFdlYiBDQSAyMDE3LjA0LjA5IDAwOjE1OjMwIEVEVCB2cG4wMTAeFw0x
<removed>
## 0ceGMQSB2NW93eLDv4u9gfWrt0FzFDG3IX1EhFlG1BIpKBPcvRPrJRytvsVYdTpc
## -----END CERTIFICATE-----

```

---

### Post by dev18 on 2017-04-09
[IMG]http://i.imgur.com/CGkfeAY.png[/IMG]


[IMG]http://i.imgur.com/5vOFM16.jpg[/IMG]

---

### Post by darkod on 2017-04-10
Wow, that client file is so long and with so little relevant info...

I have always done it the second way, but not with that DO tutorial exactly. I have always used this, which says the same thing only little shorter:
[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

It might look like much at first look, but basically once you set up your openvpn server, after that you only generate certs for clients. It's not really a big deal...

Also for client conf files I prefer to make small files with only the relevant info, without all the commented options that you never use...

For example your client config file has 10 entries for remote. Why? You only only one, pointing to the public IP or FQDN of the server where you need the client to connect to.

---

