---
title: "ubuntu server problem"
date: 2010-04-17
forum: Server Platforms
---

### Post by nilotsac on 2010-04-17
Hi 

 I have always wanted to make a linux server for my home network, and the other day I took my old Aopen XCcube, and I found a "how to make a home server in an hour" guide, so I tried:

I installed Ubuntu _9.1_0
 
I installed ssh, ftp, lamp and http in the prosess 

 I then installed NXclient, NXnode, NXserver on it
  Then I tried to get access to it by using NXclient on my laptop, and the first day a was able to get into the terminal.But now I cannot. 
  
 At first i hadn't done anything to the router settings,
but now I have tried to open port: 80 http, 21 ftp, and 22 ssh 
  Then i tried to use firestarter like in this article [http://ubuntuforums.org/showthread.php?t=736509](http://ubuntuforums.org/showthread.php?t=736509)
  but I cant get firestarter to :"Opening a listening port"
  
Now I have been stuck for 5 days trying to find different ways of connecting to it.
 The problem is that i don't really have a clue, so every time I try to follow a network configuration guide, or just a guide for setting up a server, the guide always seems to leave something out.

Do I need a static ipadress? 

When i am trying to connect to the server with NXvlient, this is what i get:
ssh: connect to host 192.168.2.5 port 22: Connection timed out

Where should i start?

---

### Post by uberlinuxnerd on 2010-04-17
> **nilotsac said:**
> Hi 

 I have always wanted to make a linux server for my home network, and the other day I took my old Aopen XCcube, and I found a "how to make a home server in an hour" guide, so I tried:

I installed Ubuntu _9.1_0
 
I installed ssh, ftp, lamp and http in the prosess 

 I then installed NXclient, NXnode, NXserver on it
  Then I tried to get access to it by using NXclient on my laptop, and the first day a was able to get into the terminal.But now I cannot. 
  
 At first i hadn't done anything to the router settings,
but now I have tried to open port: 80 http, 21 ftp, and 22 ssh 
  Then i tried to use firestarter like in this article [http://ubuntuforums.org/showthread.php?t=736509](http://ubuntuforums.org/showthread.php?t=736509)
  but I cant get firestarter to :"Opening a listening port"
  
Now I have been stuck for 5 days trying to find different ways of connecting to it.
 The problem is that i don't really have a clue, so every time I try to follow a network configuration guide, or just a guide for setting up a server, the guide always seems to leave something out.

Do I need a static ipadress? 

When i am trying to connect to the server with NXvlient, this is what i get:
ssh: connect to host 192.168.2.5 port 22: Connection timed out

Where should i start?

With all due respect, I think a good place to start would be buy a good Linux/Ubuntu book and learning some of the basics. 

Now for your questions...

For a server 'yes' it is a good idea to go for a static IP address. Does the server have a monitor? If so login via that and run ifconfig and confirm the IP address. I suspect this is where your problem lies. If you can post a bit more information regarding your architecture (e.g. Where are IPs coming from?) I will be happy to help.

Cheers

---

### Post by Iowan on 2010-04-17
If there's a DHCP server on the network, it can probably be configured to issue a "static lease" to the server (based on MAC address). Can you **ping** the server?

---

