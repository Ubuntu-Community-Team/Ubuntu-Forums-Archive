---
title: "Can't access gkrelltopd from client"
date: 2016-08-14
forum: Server Platforms
---

### Post by m-dw on 2016-08-14
I have a headless home server (Ubuntu 16.04.1) which I monitor from my desktop with gkrellm. Occasionally, I notice that the CPU utilisation on the server spikes for between 10 and 50 seconds, but by the time I've logged in and started htop, utilisation has dropped again to normal, so I have installed gkrelltopd on the server, and gkrelltop on the client.

I start the client with gkrellm -s <server.fq.dn>

I have the line "plugin-enable gkrelltopd" in my server config /etc/gkrellmd.conf

When I enable the gkrelltop plugin in the client, I momentarily see server processes (openvpn, logitech media server) in the krell, but then gkrellm crashes with the following message:
```
gkrellm segmentation fault:  gkrelltop  (update_monitor)Aborted (core dumped)
```

I've also noticed that if I disable the plugin on the server, enabling it on the client doesn't cause a crash, but the krell displays local processes on the client (as you would expect). It is therefore something to do with the client/server connection, rather than the plugin on the client. Is this a bug, or are their other steps I have to go through to allow the plugin to be queried?

---

### Post by m-dw on 2016-08-14
Resolved this myself (with help from the following article [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=543718](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=543718)

Solution was:
1) Disble plugin on server, restart gkrellmd.
2) Start gkrellm on client.
3) Enable gkrelltop plugin on client, and configure it to report top 3 services (default is 2).
4) Re-enable plugin on server and restart gkrellmd
5) Restart gkrellm on client.

---

