---
title: "Help setting up a server running Ubuntu"
date: 2015-08-23
forum: Server Platforms
---

### Post by blakeaustindailey on 2015-08-23
Hello,


A while back I used to use 12.04 LTS and a bit of 14.04 LTS on a daily basis before reverting back to Windows for the purposes of simplified gaming. I picked up some new hardware, and there were more windows supported titles back then. I've grown very rusty in the meantime. Now I have a Windows 7 Ultimate machine ... Of which I use for primary load-intensive things. HD video compiling, games, et caetera. I've come across a recent computer that's been decommissioned by a family member and gifted to me. It has an AMD Athlon II Quad-Core @3.44 Ghz or something to the extent, 2GB of ddr2 ram, and runs Windows 7 Home Premium. I need to use this for script-intensive hosting a TeamSpeak 3 Server, as well as various servers for games... Such as Arma 3 -- Which as far as the hardware itself goes, only requires handling the client-server connection and independent script handling on the server-side. I also need to be able to remote into this server over my home network, via my Windows 7 Ultimate machine so I can avoid cluttering up a desk somewhere with another monitor.


To summarize:
[B]
* Converting Windows 7 Home Premium to Ubuntu.
* Windows 7 PC has AMD Athlon II @3.44 Ghz / 2GB RAM.
* Needs to effectively handle server-client connections.
* Does NOT need to handle graphic processing
* I need to be able to remote into it from a Windows 7 PC on Home Network.
------------------------------------------
[/B]I'm not sure if this is on the wrong thread or not - It seemed the best place to start for me. Any questions, please ask if necessary. Normally I'm very capable of handling this on my own, but it's been so long I'm not very sure where to start. I need help.

---

### Post by howefield on 2015-08-23
Thread moved to the "*Server Platforms*" forum.

---

### Post by blakeaustindailey on 2015-08-23
Apologies, this seemed like a very... Troubleshooting build issues thread, so I wasn't entirely sure whether it was a general help or specialized deal. Thank you for moving it.

---

### Post by mastablasta on 2015-08-24
download and install the Ubuntu server version. what seems to be the problem? where do you get stuck?

during install mark to install openSSH server. you will be able to use putty to login remotelly or you can use sFTP (like winSCP or filezilla) to manage files safely via GUI using sFTP protocol. 

what else do you need? server management via GUI? install Ajenti for example. it's light on resoruces and does it's job rather well.


good luck and post back when you get stuck.

server installer is pretty similar to desktop one except a bit more "ugly". anyway you will be clicking the next button for the most part.

---

### Post by TheFu on 2015-08-24
Good advice from mastablasta, though I don't know anything about Ajenti (never heard of it actually).

Ah - it is a webmin clone.  Meh.  Another attack vector, IMHO. If you use it, be certain to only allow localhost connections to the web interface by using an ssh tunnel to connect only on localhost. This is easy and secure.

Use ssh, definitely. ssh is the swiss army knife for all things admin on Unix systems - and we aren't talking about the $50 knife either - this is the "do everything" $500 knife.

Secure ssh with fail2ban to block many brute force attacks, but the attackers are smarter these days, so ... 

DO NOT use passwords, just ssh-keys for all access. These keys work with everything ssh - scp, sftp, rsync, rdiff-backup, x2go, ansible - anything that uses ssh will use the keys.  More secure AND easier? How often does that happen? 

When you setup the server, you may or may not want LVM.  Usually it depends on your comfort with Linux storage. There are pros and cons to using LVM, more cons when you are new - more pros when you have experience.

---

