---
title: "Transmission-daemon trouble"
date: 2010-07-22
forum: Server Platforms
---

### Post by asai on 2010-07-22
Hi,
I have installed transmission on a headless server.
I am using transmission-daemon and connects to the webclient on the LAN. However from WAN I can't connect.
I have forwarded port 9091 in my router and it connects with the server, but i get 403:Forbidden.

Here is my settings.json file:
```
{
"alt-speed-down": 500,
"alt-speed-enabled": true,
"alt-speed-time-begin": 480,
"alt-speed-time-day": 127,
"alt-speed-time-enabled": true,
"alt-speed-time-end": 0,
"alt-speed-up": 10,
"bind-address-ipv4": "0.0.0.0",
"bind-address-ipv6": "::",
"blocklist-enabled": false,
"dht-enabled": true,
"download-dir": "\/data\/download",
"download-limit": 1000,
"download-limit-enabled": 0,
"encryption": 2,
"incomplete-dir": "\/var\/lib\/transmission-daemon\/info\/Incomplete",
"incomplete-dir-enabled": false,
"lazy-bitfield-enabled": true,
"max-peers-global": 200,
"message-level": 2,
"open-file-limit": 32,
"peer-limit-global": 240,
"peer-limit-per-torrent": 60,
"peer-port": 20683,
"peer-port-random-high": 20500,
"peer-port-random-low": 20599,
"peer-port-random-on-start": true,
"peer-socket-tos": 0,
"pex-enabled": true,
"port-forwarding-enabled": false,
"preallocation": 1,
"proxy": "",
"proxy-auth-enabled": false,
"proxy-auth-password": "",
"proxy-auth-username": "",
"proxy-enabled": false,
"proxy-port": 80,
"proxy-type": 0,
"ratio-limit": 0.2500,
"ratio-limit-enabled": true,
"rename-partial-files": true,
"rpc-authentication-required": true,
"rpc-bind-address": "0.0.0.0",
"rpc-enabled": true,
"rpc-password": "password",
"rpc-port": 9091,
"rpc-username": "transmission",
"rpc-whitelist": "127.0.0.1,*.*.*.*",
"rpc-whitelist-enabled": true,
"speed-limit-down": 1500,
"speed-limit-down-enabled": true,
"speed-limit-up": 50,
"speed-limit-up-enabled": true,
"umask": 2,
"upload-slots-per-torrent": 4,
"watch-dir": "\/data\/download",
"watch-dir-enabled": true
}
```
Any suggestions?

---

### Post by thomas_d_j on 2010-08-04
Have you checked your firewall (ufw?) settings on the server?  Also wherever you are connecting from might potentially be behind a firewall which is blocking 9091?

---

### Post by asai on 2010-08-04
Thanks for your reply.
I have installed on another server, with the exact same preferences, and it works like a charm.
So, today I will completely reinstall the server.

---

### Post by thomas_d_j on 2010-08-04
A quick 
```
sudo ufw status verbose
```
might appease my curiousity and save you a reinstall

---

### Post by asai on 2010-08-04
```
Status: inactive
```
I upgraded the server from 8.04 2 weeks ago, and I am very disapointed with the upgrade. I have also installed a desktop and some other packages that I don't need, so I think that a reinstall to 8.04 is the best solution. :)

---

