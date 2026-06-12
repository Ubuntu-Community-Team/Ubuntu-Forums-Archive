---
title: "Setting up a dhcp3 server?"
date: 2006-06-11
forum: Server Platforms
---

### Post by TTT_travis on 2006-06-11
Hi, I am attempting to setup a thin client setup using ltsp. I am stuck on setting up the dhcp3 server, please don't tell me to just RTFM, I already have and still don't understand.

Here is a my setup

[Modem]
|
[                       Router                   ]
                           ||||
                   [Ubuntu Server] [WinPC] [Mac] [Thin Client]
                           
each computer is connected directly to the router

My ubuntu server will be running ltsp server and dhcp3-server, this computer has 1 NIC Card, 

the winpc will get an ip from ubuntu server
the mac will get an ip from ubuntu server

the thin client gets and ip as well as the firmware etc. from ubuntu server

The router is running on 192.168.1.1

could some tell me with intense detail what I need todo? (settings to be changed, config files, I need to know exactly what to put in the dhcp3 config file aswell as any changes to the interfaces or hosts config files and exactly what they need to be. I know this is asking a lot, but I need assistance.

Travis

---

