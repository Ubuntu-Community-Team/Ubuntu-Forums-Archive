---
title: "OpenVPN Mac Connection problem"
date: 2012-03-20
forum: Server Platforms
---

### Post by RyanRahl on 2012-03-20
Hi, I have an Ubuntu 11.04 server running OpenVPN with 5 clients that connect regularly(including myself) with no issues at all. There are 2 Ubuntu desktops using the Network Manager module for OpenVPN, 2 Macbooks using TunnelBlick and one Windows 7 using OpenVPN GUI. This customer uses the VPN for remote desktop in their office network. Anyhow, I went to my customer's office to set up a 6th machine that is a Macbook and the installation of Tunnelblick and the keys went fine as usual but in this case for some reason the software sometimes hangs on connecting, if I click disconnect and connect again usually it will work. But the real problem is that once I connect I have a few second window for it to actually work. Basically when I connect, if I ping a host on the network it gets through about 2~4 pings and then errors out saying the host is unreachable and I get a similar host unreachable error when attempting to connect to a remote desktop. The config file I am using is an exact duplicate of the file I use on the other Macbooks aside from the names of the user certificate and key so I'm sure the configuration is correct. I upped the verbosity of the log file on the server end and it doesn't show any activity after the machine has 'dropped' the connection and can't communicate so I know the communication isn't being blocked and the logfile on the client doesn't show anything either. The VPN status says it's still connected but I can not communicate with anything on the network. Has anyone else had this kind of an issue? I am going to try and re-install the Tunnelblick software again tomorrow and see what happens. I am using TAP interfaces and ethernet bridging. Any input would be great because I am not a Mac expert and this is a really important account and I really would like to get this working. Thanks.

---

