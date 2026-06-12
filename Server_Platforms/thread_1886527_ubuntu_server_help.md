---
title: "ubuntu server help"
date: 2011-11-25
forum: Server Platforms
---

### Post by Tasha Richardson on 2011-11-25
Hi everyone 
I'M wanting a server nothing real hard just a file server or maybe a media server. I bought a old dell p4 PC for $50 bucks I was wondering what the system requirements are for Ubuntu server 11.10? I read on the INTERNET it was 128 mb ram this pc is good but only has 256 mb of ram and this is really low.I also read that you need to have a monitor on it at all times to run do i need to run one on it I know Ubuntu desktop has to have one what about the server?Also what do i need to install or do i need to install anything to make this a file server.

I was looking into using lbuntu for it's low system requirements to make this but as it is a desktop system i didn't know if it would work.Thanks

---

### Post by darkod on 2011-11-25
1. You will need a monitor first time when setting it up but later it does not have to have a monitor connected.

2. If you use the server cd to install, once the core files are installed it will ask you for additional roles you want to install. As minimum, select OpenSSH Server and Samba Server.
OpenSSH will allow you access through your local network without needing to connect monitor, etc.
Samba is the file server application.

Be advised that the server system is only a text command prompt system. It does not have a GUI but since you don't want to run a monitor on it, it doesn't matter I guess.

---

### Post by Doug S on 2011-11-25
Yes, the Ubuntu 11.10 server guide lists 128 MegaBytes as the minimum memory. I am running Ubuntu Server edition 11.10 on a 15 year old 200 Mhz computer with 128 Megabytes of memory. I use the computer just as a test computer. I only upgraded from Ubuntu server version 6.06, that had been running on it for several years for these reasons: To see if it could be done; So that my test machine would be a little more current; And so that I could claim to have the most pathetic 11.10 server in all the land (joke).
I am not claiming that it works very well, but it is working, albeit ssslllooowwwlllyyy.
Installation was pretty slow also.
This computer is not a router, nor do I have samba running on it, although I will probably try to get samba going some day. I use WinSCP for moving files back and forth, and transfer rates are not so bad. Currently, I do have a very high number of packet collisions, and just haven't had time to investigate yet.
I hope this helps.

---

