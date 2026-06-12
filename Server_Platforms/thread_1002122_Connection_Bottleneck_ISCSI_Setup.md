---
title: "Connection Bottleneck ISCSI Setup"
date: 2008-12-04
forum: Server Platforms
---

### Post by Biker803 on 2008-12-04
Hey guys,

I'm using Open-ISCSI with Ubuntu Server 8.10 64-bit installed on a Dell PowereEdge 1850 Server, and I'm trying to figure out why I'm getting a bottleneck when serving files with many open concurrent connections.

The server is the initiator connecting to a 14TB NTFS partition (read only) of a SAN and they are directly connected by Ethernet.

I also run Apache on the server (have tried Lighttpd as well) that has an alias set up so that when a user requests [http://server/files/](http://server/files/) it goes to /iscsi/files/. It's serving out of an additional NIC of course (both NICs in server are 1000gbit full duplex).

Here lies my problem. I have everything working flawlessly with the auto mounting at boot up, downloading files through the web server, etc... it all works great, except that after about 200 simultaneous connections the server locks up and I can't refresh a simple static .htm page that is on the SAN. I'm mainly serving video content that could range from 2mb to 100mb a piece, and I expect anywhere from 100-2000 connections to the server at any given time.

Now, I know that this process does work as I am currently doing it on a Windows box. The box has no problem taking all of the traffic and serving many files simultaneously. The Windows box is also on a Dell PowerEdge 1850 (IDENTICAL SERVER)... and it has no problems. I have a Gigabit connection out to the public so I expect to be able to max out at 600-700mbits during peak loads.

Anyone have any suggestions? Should I be updating network drivers, iscsi settings, apache/lighttpd settings, anything? I'm really at a loss here and don't have a ton of experience in Linux so this is all a learning process. I've already tried raising MaxClients so I don't think I'm hitting that limit -- I'm not really sure what to do here.

Thanks for your help!

---

