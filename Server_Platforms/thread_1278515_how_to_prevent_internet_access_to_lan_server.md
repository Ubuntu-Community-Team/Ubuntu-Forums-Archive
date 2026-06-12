---
title: "how to prevent internet access to lan server"
date: 2009-09-29
forum: Server Platforms
---

### Post by chinaski on 2009-09-29
I have a file and print server based on Ubuntu Jaunty 9.04 and few clients over my home lan, I would like to prevent server to be exposed on the Internet while having full lan access, but can't figure out how

I searched and found only ways to prevent specific users to surf the web, but it's too complicated I just need to prevent internet trafic, I guess it can be done by modifying /etc/hosts (or other config file) but I cannot figure out how

any help is much appreciated

---

### Post by openfly on 2009-09-29
Well in theory if they are all on the same switch.  You can just remove the default / all routing information from the file / print server.  Then provide hosts file entries to all your clients.  And that would probably work fine.

However, the correct answer here is to use a firewall.

---

### Post by bab1 on 2009-09-29
> **chinaski said:**
> I have a file and print server based on Ubuntu Jaunty 9.04 and few clients over my home lan, I would like to prevent server to be exposed on the Internet while having full lan access, but can't figure out how

Use NAT.  If you have NAT'd the LAN (for private addresses) then the only way to initiate contact with a host (server or client) is with port forwarding implemented.> 

I searched and found only ways to prevent specific users to surf the web, but it's too complicated I just need to prevent internet trafic, I guess it can be done by modifying /etc/hosts (or other config file) but I cannot figure out how.  ...



Outbound traffic should still be allowed with NAT.  That should not present a problem to your server.  I have 2 servers on my LAN with no problems.

Inbound and outbound initiated connectivity are 2 different things.  Are you sure of what want to do?

---

### Post by Iowan on 2009-09-29
How do you connect to Internet? A related question - how do you get IP address - static or DHCP (probably static for server... but what subnet). If your server uses a "private network" address, (as **bab1** mentioned) you'd need to enable port-forwarding to reach it from "outside".

---

### Post by bab1 on 2009-09-29
In rereading the OP, I see some errors of terminology.  To my way of thinking "... and few clients over my home lan" means we are servicing clients in the LAN (as in Client/Server) rather than **foreign hosts accessing my LAN** as in *your business clients*.

Either way NAT is the key.  If you have business clients that wish to access your server then as was stated before, you will need to open specific ports that the applications use via port forwarding.

Iowan has brought up a point, *How ARE you connected to the internet?*  And more importantly, what are you doing to protect the server now.  

If it is connected via a standard ISP home connection then you might need to look into DynDNS if the IP address is provided by DHCP.

---

### Post by cariboo on 2009-09-29
I run my home network with a Linksys wrt54gs and an unmanaged switch. My home server has no ports open through the router, so no one can access it from the internet.

---

### Post by Krijk on 2009-09-30
> **cariboo907 said:**
> I run my home network with a Linksys wrt54gs and an unmanaged switch. My home server has no ports open through the router, so no one can access it from the internet.

I would use a firewall on the server and maybe an IPS with it, but since you're using wireless somebody might access your network anyway.

---

### Post by chinaski on 2009-10-13
thanks all for your replies

I am so sorry for my delay in replying back, but here I am

I have installed the server but the owner asked me to install a DE too and have Internet access, she said she'd prefer to have a full machine just in case she might need it to surf the web

I told her maybe it was not a good idea but I also thought:

1) she is the owner of the machine,and she's been warned about the risks. her choice
2) she might get confident with Linux and maybe want it on desktop machines in the future

I thank you all for your replies, Ubuntu (Linux) community is what really make this OS superior, beyond the tech stuff :D

cheers,
Cris

---

### Post by Iowan on 2009-10-13
> **chinaski said:**
> I told her maybe it was not a good idea...I  agree that using a server as a workstation probably isn't the best idea... 
(but - as bad as you'd like to say it, "I told you so" probably won't soothe a client who just wants you to make their mistake go away ;) )

---

