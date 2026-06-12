---
title: "SSH Tunnel problem"
date: 2017-08-21
forum: Server Platforms
---

### Post by rushhh2 on 2017-08-21
Hi,

I'm trying to connect to a server trough a gateway but the ending server refuse the connection :

c:\Program Files\PuTTY>plink.exe -v xxx@192.168.100.1 -nc root@172.16.4.1:22
Connecting to 192.168.100.1 port 22
We claim version: SSH-2.0-PuTTY_Release_0.70
Server version: SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
We believe remote version has SSH-2 channel request bug
Using SSH protocol version 2
Doing ECDH key exchange with curve Curve25519 and hash SHA-256
Server also has ssh-ed25519/ecdsa-sha2-nistp256/ssh-dss host keys, but we don't know any of them
Host key fingerprint is:
ssh-rsa 2048 72:2e:8b:57:44:f1:64:d9:5e:34:f3:87:c0:cc:9c:85
Initialised AES-256 SDCTR client->server encryption
Initialised HMAC-SHA-256 client->server MAC algorithm
Initialised AES-256 SDCTR server->client encryption
Initialised HMAC-SHA-256 server->client MAC algorithm
Pageant is running. Requesting keys.
Pageant has 1 SSH-2 keys
Using username "xxx".
Trying Pageant key #0
Authenticating with public key "xxx" from agent
Sending Pageant's response
Access granted
Opening connection to root@172.16.4.1:22 for main channel
Server refused to open main channel: Administratively prohibited [open failed]
FATAL ERROR: Server refused to open main channel: Administratively prohibited [open failed]

the following parameters are enabled :
AllowTCPForwarding yes
PermitOpen any
PermitTunnel yes

Please help if you have an idea :)

---

### Post by TheFu on 2017-08-21
Remote root isn't allowed in Ubuntu.
Use a different userid, then sudo.

---

### Post by rushhh2 on 2017-08-21
it's OK thanks !

---

