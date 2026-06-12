---
title: "OpenVPN tries to start multiple (old) services"
date: 2023-04-04
forum: Server Platforms
---

### Post by porkpiehat2 on 2023-04-04
Hi all,

I have had OpenVPN server running for a long time on a mini-PC running Ubuntu Server 20.04. Some time ago, I wanted to experiment running multiple configurations to run both TCP and UDP protocols on multiple ports. That did not work, I tried to revert it, but now I have issues running a single service again. It's been some time, so I cannot exactly recall what I did that time.

Now, whenever I restart the system, OpenVPN automatically attempts to start multiple configuration files that are no longer present. The folder '/etc/openvpn/server' only has one configuration file in it: 'udp994.conf'. The journalctl entries however show that on boot, OpenVPN still attempts to start multiple non-existent configurations like 'server.conf', 'tcp443.conf' and 'udp1194.conf'.
I cannot for the life of me find where I have configured this, so I hope you can help with this.

It seems like a trivial problem, just I cannot find it. Hope that someone can help with this.

Here is the output of journalctl after a reboot:
```

Apr 04 16:24:41 prometheus systemd[1]: openvpn-server@server.service: Scheduled restart job, restart counter is at 20.
Apr 04 16:24:41 prometheus systemd[1]: Stopped OpenVPN service for server.
Apr 04 16:24:41 prometheus systemd[1]: Starting OpenVPN service for server...
Apr 04 16:24:41 prometheus openvpn[1839]: Options error: In [CMD-LINE]:1: Error opening configuration file: server.conf
Apr 04 16:24:41 prometheus openvpn[1839]: Use --help for more information.
Apr 04 16:24:41 prometheus systemd[1]: openvpn-server@server.service: Main process exited, code=exited, status=1/FAILURE
Apr 04 16:24:41 prometheus systemd[1]: openvpn-server@server.service: Failed with result 'exit-code'.
Apr 04 16:24:41 prometheus systemd[1]: Failed to start OpenVPN service for server.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@udp1194.service: Scheduled restart job, restart counter is at 20.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@udp994.service: Scheduled restart job, restart counter is at 20.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@server.service: Scheduled restart job, restart counter is at 20.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@tcp443.service: Scheduled restart job, restart counter is at 20.
Apr 04 16:24:42 prometheus systemd[1]: Stopped OpenVPN connection to server.
Apr 04 16:24:42 prometheus systemd[1]: Starting OpenVPN connection to server...
Apr 04 16:24:42 prometheus systemd[1]: Stopped OpenVPN connection to tcp443.
Apr 04 16:24:42 prometheus systemd[1]: Starting OpenVPN connection to tcp443...
Apr 04 16:24:42 prometheus systemd[1]: Stopped OpenVPN connection to udp1194.
Apr 04 16:24:42 prometheus systemd[1]: Starting OpenVPN connection to udp1194...
Apr 04 16:24:42 prometheus systemd[1]: Stopped OpenVPN connection to udp994.
Apr 04 16:24:42 prometheus systemd[1]: Starting OpenVPN connection to udp994...
Apr 04 16:24:42 prometheus ovpn-server[1843]: Options error: In [CMD-LINE]:1: Error opening configuration file: /etc/openvpn/server.conf
Apr 04 16:24:42 prometheus ovpn-server[1843]: Use --help for more information.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@server.service: Main process exited, code=exited, status=1/FAILURE
Apr 04 16:24:42 prometheus systemd[1]: openvpn@server.service: Failed with result 'exit-code'.
Apr 04 16:24:42 prometheus systemd[1]: Failed to start OpenVPN connection to server.
Apr 04 16:24:42 prometheus ovpn-udp994[1846]: Options error: In [CMD-LINE]:1: Error opening configuration file: /etc/openvpn/udp994.conf
Apr 04 16:24:42 prometheus ovpn-udp994[1846]: Use --help for more information.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@udp994.service: Main process exited, code=exited, status=1/FAILURE
Apr 04 16:24:42 prometheus systemd[1]: openvpn@udp994.service: Failed with result 'exit-code'.
Apr 04 16:24:42 prometheus systemd[1]: Failed to start OpenVPN connection to udp994.
Apr 04 16:24:42 prometheus ovpn-tcp443[1844]: Options error: In [CMD-LINE]:1: Error opening configuration file: /etc/openvpn/tcp443.conf
Apr 04 16:24:42 prometheus ovpn-tcp443[1844]: Use --help for more information.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@tcp443.service: Main process exited, code=exited, status=1/FAILURE
Apr 04 16:24:42 prometheus systemd[1]: openvpn@tcp443.service: Failed with result 'exit-code'.
Apr 04 16:24:42 prometheus systemd[1]: Failed to start OpenVPN connection to tcp443.
Apr 04 16:24:42 prometheus ovpn-udp1194[1845]: Options error: In [CMD-LINE]:1: Error opening configuration file: /etc/openvpn/udp1194.conf
Apr 04 16:24:42 prometheus ovpn-udp1194[1845]: Use --help for more information.
Apr 04 16:24:42 prometheus systemd[1]: openvpn@udp1194.service: Main process exited, code=exited, status=1/FAILURE
Apr 04 16:24:42 prometheus systemd[1]: openvpn@udp1194.service: Failed with result 'exit-code'.
Apr 04 16:24:42 prometheus systemd[1]: Failed to start OpenVPN connection to udp1194.

```

---

