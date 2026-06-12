---
title: "Need help setting password for transmission cli!"
date: 2010-04-21
forum: Server Platforms
---

### Post by big_danmahony on 2010-04-21
Can someone please help me?
I've been able to access my transmission torrent remotely for some time now and I was wondering, how do I enable a password?
I'm using ubuntu server edition 9.10 if that helps.

here is my transmission-daemon/settings.json

    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "dht-enabled": true,
    "download-dir": "\/home\/dan\/Downloads",
    "encryption": 1,
    "lazy-bitfield-enabled": true,
    "message-level": 2,
    "open-file-limit": 32,
    "peer-limit-global": 240,
    "peer-limit-per-torrent": 60,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": false,
    "peer-socket-tos": 0,
    "pex-enabled": true,
    "port-forwarding-enabled": true,
    "preallocation": 1,
    "proxy": "",
    "proxy-auth-enabled": false,
    "proxy-auth-password": "",
    "proxy-auth-username": "",
    "proxy-enabled": false,
    "proxy-port": 80,
    "proxy-type": 0,
    "ratio-limit": 2.0000,
    "ratio-limit-enabled": false,
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "{ef40c74e5e444448e3933c28011a02ca99edf6126CXdMklQ",
    "rpc-port": 9091,
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": false,
    "speed-limit-down": 75,
    "speed-limit-down-enabled": true,
    "speed-limit-up": 25,
    "speed-limit-up-enabled": true,
    "umask": 18,
    "upload-slots-per-torrent": 14

If anyone could help me with this it would be greatly appreciated.
Thank you for your time.

Dan.

---

### Post by big_danmahony on 2010-04-21
I got it! only just after I posted.
Don't heckle me, I already feel stupid for posting. :P

All I did was change these settings in my .json file

   "rpc-authentication-required": true,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "**PASSWORD GOES HERE**",
    "rpc-port": 9091,
    "rpc-username": "dan",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": false,
    "speed-limit-down": 75,
    "speed-limit-down-enabled": true,
    "speed-limit-up": 25,
    "speed-limit-up-enabled": true,
    "umask": 18,
    "upload-slots-per-torrent": 14
}

---

