---
title: "Connecting to mssql server"
date: 2014-07-31
forum: Server Platforms
---

### Post by janis-roze1 on 2014-07-31
Hi everyone 

i need to conect to a ip address where my mssql server is located. Servers ip 192.168.0.42:1443 but i am not in the same network but i have access to a ubuntu machine in that local network with a outer ip address 81.242.125.34:8022! is it possible to connect to db through the ubuntu machine, create a tunnel or somehow.


the idea is:

my laptop ->connects to ubuntu device behind router (external_ip:8022)(machines internal_ip 192.168.0.73)-> through ubuntu machine connect to mssql server (internal_ip 192.168.0.42)

---

### Post by TheFu on 2014-07-31
There are many different ways to accomplish this, but some are highly non-secure. If you'd like to be hacked, use one of those
Or .... better, assume that 8022 is ssh access, not MYSQL!!!!!!!

a) setup a VPN (openvpn) to the server and tunnel all traffic through that.
b) use ssh and do everything local on the remote machine
c) use an ssh tunnel (the man page explains)  - something like ssh -L 50822:81.242.125.34:8022 .... I'd have to look up the exact command.
d) setup a remote desktop with something like x2go/freenx running on the remote system.

So, if you really need to have the DB client external, then only the VPN or SSH tunnel are viable.

---

