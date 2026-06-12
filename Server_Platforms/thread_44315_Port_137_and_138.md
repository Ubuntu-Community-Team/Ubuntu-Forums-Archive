---
title: "Port 137 and 138"
date: 2005-06-25
forum: Server Platforms
---

### Post by ron126 on 2005-06-25
My firestarter keeps producing a block connection logs. The source of these inbound connections are from various computers in my network (on the same LAN as mine). The ports are either 137 and 138  and the service is SMB (UDP). And its destination is usually x.x.x.255. 

What are they? Should i do anything or just ignore it?

---

### Post by crashtest on 2005-06-25
[QUOTE=ron126]My firestarter keeps producing a block connection logs. The source of these inbound connections are from various computers in my network (on the same LAN as mine). The ports are either 137 and 138  and the service is SMB (UDP). And its destination is usually x.x.x.255. 

What are they? Should i do anything or just ignore it?[/QUOTE]


Sounds like you have a Windows machine on the network that is sharing files.  Windows systems "advertise" the resources they are sharing by sending broadcast messages.  Sending to x.x.x.255 is a broadcast.  SMB (Server Messaging Blocks) is the name of the protocol that windows uses for file sharing.  On Linux systems, SAMBA is a reverse-engineered version of the same protocol.   So it is either a Windows machine, or another Linux machine running a SAMBA server.

---

### Post by LordHunter317 on 2005-06-25
[QUOTE=crashtest]  Windows systems "advertise" the resources they are sharing by sending broadcast messages.[/quote]This isn't actually true, FWIW.  It's not quite relevant here.  The only thing they "advertise" is their existence on the network to the browse master.  But that's it.

>   Sending to x.x.x.255 is a broadcast.Not necessarily true, but almost always on a home network.  May not be so on a corporate network.

---

### Post by ron126 on 2005-06-25
Ok, didn't sound like a threat

---

### Post by ron126 on 2005-06-25
Good news, didn't sound like a threat

---

### Post by crashtest on 2005-06-26
[QUOTE=LordHunter317]This isn't actually true, FWIW.  It's not quite relevant here.  The only thing they "advertise" is their existence on the network to the browse master.  But that's it.

Not necessarily true, but almost always on a home network.  May not be so on a corporate network.[/QUOTE]

It has been several years since I did much windows work - I barely touch windows machines at work now, dealing mostly with Linux and Unix, so I guess my knowledge may be rusty or incomplete.  I did a little digging on this because I was curious about what you said.  Here's what I found:

-when a wintel machine boots up it broadcasts its NetBIOS name on the local subnet to register with the browse master
-A computer with resources broadcasts an announcement every 12 minutes to refresh the browse lists.
-browser traffic is normally done by broadcast, over UDP port 137.  (If there is a WINS server on the network, browser traffic will be directed, not broadcast. ) 

Windows machines on a network are normally very "chatty" and may fill up to 30% of the pipe with this background traffic.  Don't even get me started on the subject of Browser elections...  :-)

You are correct about x.x.x.255 not always being a broadcast address, but as a general rule of thumb it holds true.  (My previous company used a public /26 subnet, so the broadcast address there was x.x.x.63)

Not wanting to mislead the original poster about what his firewall is logging, let me ask you:  What do you think the UDP port 137 / 138  SMB traffic is likely to be? Windows file and print sharing traffic?  What about if he is running a SAMBA server on the Linux machine - wouldn't the incoming client requests use port 137 or 138?  The SAMBA server itself would run nmbd and smbd,  and I know nmbd will use port 137, but I'm not sure about smbd...

---

### Post by LordHunter317 on 2005-06-26
It's SMB over NetBIOS/TCP traffic.  Samba setup as a server will broadcast it, as will Windows.  It's likely harmless and can be safely ignored.  

Port 137 is netbios-ns, and used for doing NetBIOS name lookups.    Port 138 is netbios-dgm, and used for the browse elections and other broadcasts.  Both are normally used in the browse announcement process.  

There are a few worms that run over these ports, doing IPC attacks against Windows machines.  However, they look like normal SMB traffic (because they are) so you can't tell if the traffic is malicious or not.

But the odds of that being the case is terribly small, if his machines are all up to date.  I'd be money on it being perfectly normal SMB traffic.

If you have modern enough versions of Samba (which Ubuntu includes) and Windows, you can disable NetBIOS/TCP and only use CIFS, which cuts down on the traffic substantially.  It requires working DNS though.

---

### Post by crashtest on 2005-06-26
Thanks for the information Lordhunter.

---

