---
title: "Can't ping by hostname but ip ok"
date: 2012-09-28
forum: Server Platforms
---

### Post by Jaban on 2012-09-28
Hi all,

I have a small local network consisting of my ubuntu server 12.04 (upgrade from 11.04), a windows machine running vista and my routeur/modem dsl box in the middle. The server is linked to the box by a cable and the laptop is linked by wifi. Internet access from all is working just fine. I can ping everything from all machines using the ip, and everything from the outside world using the hostname (i.e. [www.ubuntuforums.org]("http://www.ubuntuforums.org") from the server).

But I simply cannot ping from my laptop to my server using the server hostname!!!

I have setup a static ip address in /etc/hosts on the server and have the following config:
127.0.0.1       localhost
127.0.0.1       ubuntu-server
192.168.1.45 server_name

if I ping from the server itself using server_name, then it works fine. If I try from my windows machine, it says it can't find this server.

Would anyone know how to resolve this?

Cheers,
Jab

---

### Post by volkswagner on 2012-09-28
You would need a local DNS server running to get local name resolution.  Some routers can do this with DNS_masq.

A simple approach you have started.  You have edited /etc/host on the Ubuntu machine, but you need to do It on the client machine as well.

For windows look in $/system32/drivers/etc/hosts on newer systems.  Editing this file with UAC can be annoying.  I usually open Notepad in Administrator mode then open the file from within notepad.

---

