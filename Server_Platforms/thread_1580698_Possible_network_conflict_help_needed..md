---
title: "Possible network conflict help needed."
date: 2010-09-23
forum: Server Platforms
---

### Post by Quistserver on 2010-09-23
Hello, i have problem with a special port. The port is 7172 ans is used to connect to an game server that I'm hosting on ubuntu server 10.4.

The problem is that to login on the "character list" the port 7171 is used, this works without any problem. But to login on the game the port 7172 is used and this doesn't work. I've even forwarded the ports and done everything like it should be done. Here is a print of my netstat:
___________________________________________________________
root@server:/home/server# netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.1.1:7171          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:7171          0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.7:7171        0.0.0.0:*               LISTEN
tcp        0      0 127.0.1.1:7172          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:7172          0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.7:7172        0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
root@server:/home/server#
_____________________________________________________________

The ip I'm using in the game server config is 192.168.1.7, because my global ip doesn't work. Please reply if you have any idea how to fix this, I'm very grateful for any kind of help!

---

### Post by scrooge_74 on 2010-09-23
You need to provide more info on your setup, things like:

the clients are outside or inside lan?
firewall config
type of game <<--maybe someone has done it before

---

### Post by Quistserver on 2010-09-24
The clients that can't connect are outside LAN. The whole network has about 5 computers on it.
The firewall is cofigured to allow port 7171 7172 on the Ubuntu computer (192.168.1.7).
The game that I'm trying to host a server on is Tibia.

---

### Post by R.Bucky on 2010-09-24
You have mentioned everything but Port Forwarding on the router. Have you directed external traffic to the correct machine?

---

### Post by Quistserver on 2010-09-24
Yes I've forwarded the ports 7171 and 7172 to the unbuntu server computer in the port forwarding configuration on the router. The router is an NETGEAR CG3100 if it helps.
The port 7171 works, it's the port 7172 that i have a problem with.

---

### Post by scrooge_74 on 2010-09-24
Those that port requieres to be a tcp or udp conection? That could be it.  Did you check that the server is allowing access to that port also?

---

### Post by Quistserver on 2010-09-24
I'm not sure so i forwarded both udp and tcp and yes the server is allowing access to the port, i think. I'm not 100% on how to check these things on ubuntu server

---

### Post by scrooge_74 on 2010-09-24
you can use nmap from another machine outside the network and check the results of the port scanning

Try telneting into the port

---

