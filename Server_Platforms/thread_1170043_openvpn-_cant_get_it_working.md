---
title: "openvpn- cant get it working"
date: 2009-05-25
forum: Server Platforms
---

### Post by lockmac on 2009-05-25
Hi there. Trying to set up an openvpn server on ubuntu.
Its showing me the following when trying to connect:

```
Tue May 26 11:16:19 2009 OpenVPN 2.1_rc16 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on May 17 2009
Tue May 26 11:16:19 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Tue May 26 11:16:20 2009 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Tue May 26 11:16:20 2009 LZO compression initialized
Tue May 26 11:16:20 2009 Attempting to establish TCP connection with 220.245.130.173:1194
Tue May 26 11:16:20 2009 TCP connection established with 220.245.130.173:1194
Tue May 26 11:16:20 2009 TCPv4_CLIENT link local: [undef]
Tue May 26 11:16:20 2009 TCPv4_CLIENT link remote: xxx.xxx.xxx.xxx:1194
Tue May 26 11:16:20 2009 Connection reset, restarting [0]
Tue May 26 11:16:20 2009 SIGUSR1[soft,connection-reset] received, process restarting
Tue May 26 11:16:25 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Tue May 26 11:16:25 2009 Re-using SSL/TLS context
Tue May 26 11:16:25 2009 LZO compression initialized
Tue May 26 11:16:25 2009 Attempting to establish TCP connection with 220.245.130.173:1194
Tue May 26 11:16:25 2009 SIGTERM[hard,init_instance] received, process exiting

```

My Server config is:

```
local 10.0.0.4
port 1194
proto tcp
dev tap0
ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/easy-rsa/2.0/keys/server.crt
key /etc/openvpn/easy-rsa/2.0/keys/server.key
dh /etc/openvpn/easy-rsa/2.0/keys/dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 10.0.0.4 255.255.255.0 10.0.0.5 10.0.0.9
client-to-client
keepalive 10 120
cipher AES-128-CBC
tls-auth /etc/init.d/ta.key 0
comp-lzo
max-clients 5
persist-key
persist-tun
status openvpn-status.log
verb 3
plugin /usr/lib/openvpn/openvpn-auth-pam.so login

```

My Client config is:
```
client 
dev tap 
proto tcp 
# change this to your server's address 
remote vpn-gw.xxxx.com 1194 
resolv-retry infinite 
nobind
persist-key 
persist-tun 
# Point the key and crt files to  
# the ones for this user 
tls-client
ca ca.crt 
cert lock.crt 
key lock.key 
#ensure that we are talking to a server 
ns-cert-type server
#confirm we are talking to the correct server 
tls-auth ta.key 1
# Select a cryptographic cipher. 
# If the cipher option is used on the server 
# then you must also specify it here. 
cipher AES-128-CBC 
# Enable compression on the VPN link. 
comp-lzo 
#fragment large packets 
# I found I needed this for some games but it is 
# not required
#fragment 1400  
# enable user/pass authentication

```

Any ideas why? Im not very good with linux so im sure its something simple.

BTW, i followed this tutorial [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

Thanks guys

---

### Post by gombadi on 2009-05-25
> 
Tue May 26 11:16:20 2009 TCPv4_CLIENT link remote: xxx.xxx.xxx.xxx:1194
Tue May 26 11:16:20 2009 Connection reset, restarting [0]


Is there anything in the log files on the server to say why if dropped the connection?

---

### Post by lockmac on 2009-05-26
Hi. Where abouts is this log file for openvpn?

---

### Post by kvizz on 2009-05-26
check /var/log/syslog

---

### Post by lockmac on 2009-05-26
```
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: Expected Remote Options hash (VER=V4): '29f6c8b2'
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: TCP connection established with 203.100.246.146:49338
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: Socket Buffers: R=[131072->131072] S=[131072->131072]
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: TCPv4_SERVER link local: [undef]
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: TCPv4_SERVER link remote: xxx.xxx.xxx.xxx:49338
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: 203.100.246.146:49338 TLS: Initial packet from 203.100.246.146:49338, sid=9f1099ac 5843c108
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: 203.100.246.146:49338 Authenticate/Decrypt packet error: packet HMAC authentication failed
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: 203.100.246.146:49338 TLS Error: incoming packet authentication failed from 203.100.246.146:49338
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: 203.100.246.146:49338 Fatal TLS error (check_tls_errors_co), restarting
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: 203.100.246.146:49338 SIGUSR1[soft,tls-error] received, client-instance restarting
May 26 10:13:33 lock-ubuntu ovpn-server[4782]: TCP/UDP: Closing socket
May 26 10:13:38 lock-ubuntu ovpn-server[4782]: MULTI: multi_create_instance called
May 26 10:13:38 lock-ubuntu ovpn-server[4782]: Re-using SSL/TLS context
May 26 10:13:38 lock-ubuntu ovpn-server[4782]: LZO compression initialized
May 26 10:13:38 lock-ubuntu ovpn-server[4782]: Control Channel MTU parms [ L:1592 D:168 EF:68 EB:0 ET:0 EL:0 ]
May 26 10:13:38 lock-ubuntu ovpn-server[4782]: Data Channel MTU parms [ L:1592 D:1450 EF:60 EB:135 ET:32 EL:0 AF:3/1 ]

```

---

### Post by kvizz on 2009-05-26
1) try to use openvpn without tls - just to check everything else works fine
2) there is an option (don't remember exactly on server or on client), something about tls timeout, try to encrease it to 120 for example. i've had this issue on some gprs-modems some time ago and this was useful for me

---

### Post by lockmac on 2009-05-26
> **kvizz said:**
> 1) try to use openvpn without tls - just to check everything else works fine
2) there is an option (don't remember exactly on server or on client), something about tls timeout, try to encrease it to 120 for example. i've had this issue on some gprs-modems some time ago and this was useful for me

Hi. I belive I have fixed it. I think i must have regenerated the key files accidently when i was rooting around.

Anyways, just a question, why cant you connect to a VPN when you ae on the same network you are connecting to?

I havnt tested that this works externally, but i am on the same network as my vpn server and the vpn has connected fine and got its IP address....

---

