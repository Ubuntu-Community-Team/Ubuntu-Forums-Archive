---
title: "Transmission-daemon configuration problem"
date: 2011-03-10
forum: Server Platforms
---

### Post by pyedog on 2011-03-10
I have recently installed a base Ubuntu system on an old netbook due to limited disk space and I'm using it as a headless server.

I have installed transmission-daemon and the following lines as such in .config/transmission-daemon/settings.json are as follows:

    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "***", (password hidden in case it's private)
    "rpc-port": 9091,
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1 192.168.1.*",
    "rpc-whitelist-enabled": false,

and restarted the daemon using /etc/init.d/transmission restart. When I browse to my server's address port 9091 in my desktop browser I get a 403 error telling me to disable  the IP address whitelist or add my address to it.

Anyone got any ideas I can try for troubleshooting or for what the problem may be? Thanks :)

---

### Post by pyedog on 2011-03-10
Found out the config file is duplicated in /var/lib/transmission-daemon/info/settings.json and transmission-daemon uses that for some reason.

---

