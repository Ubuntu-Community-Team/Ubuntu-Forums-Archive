---
title: "[SOLVED] Squid native user authetication"
date: 2007-03-22
forum: Server Platforms
---

### Post by xyrer on 2007-03-22
Hi, I've been looking evrywhere but can't find exactly what I want so I hope someone knows what I can look for.
I have a Windows machine serving as a proxy using commercial product Wingate, the machine has to be Windows because there's a VPN software provided to us and only runs in windows, I can't get access to VPN connection specs so I can't look for a replacement.
I was thinking on replacing Wingate with squid for NT, wich works perfect in XP, the dilema here and the only thing missing is the user authentication, in Wingate we have a user database and a login page evrytime they try to browse the internet, the login page calls a telnet window wich asks for login and password, as long as the telnet is open the user can have access to the internet.
The main problem is that this telnet connections not everytime work, most of the time the user stays logged in and any "guest" who can access the pc can navigate and the user looged in gets the blame for whatever the "guest" does, it's one of the main reasons to change the proxy server.

Now, I have seen NoCat and Wifidog for hotspots and I would certainly install one of them, but they claim to require a linux OS, wich leads finally to my question. Is squid capable of doing something like what I want? The users are created by me so I only need them to put username and password to navigate, I don't need them to change passwords, create accounts or anything as such, just to identify themselves.
If squid can't do it, maybe there is some opensource software OS independent so I can put it along with the squid for Windows?

Thanks to everyone for your time.

---

### Post by munwin on 2007-03-26
Are your users on a Windows domain ?
If so, I think I can help.
I have Squid running here (both on Windows and Ubuntu), that verifys the users credentials, and logs their AD Username. All transparently (if they use IE - not sure about FireFox on Windows). I can browse from my Ubuntu box, using the proxy, and I have to enter my AD Username and Password the initial time, but then it's cached.

I went one further though - I have the squid logs parsed and entered into a MySQL database, that I have some web reporting done, too....

---

### Post by xyrer on 2007-03-26
Mmm, actually I don't know what AD stands for, and no, I don't use domain here, only workgroups, simple network, I don't find any use to Windows domains.
I just thought that maybe I could replace that wingate program, but until now, it's the only one that gives me user authentication for only the time the telnet window is open (well, most of the times).
I will keep looking for something that might help me, until the time I can replace the windows machine with a ubuntu one.

Thanks anyway.

---

### Post by munwin on 2007-03-27
Maybe try to find an "ident" program for the Windows machines. It runs as a service, and Squid can query it for the username of the person using the machine.
The only caveat is (in our case) we use Terminal Services, and when more than on eperson is using the server, ident doesn't work properly. It is design for one user, one machine.
It may be OK in your situation.

---

### Post by xyrer on 2007-03-27
Well, using a client program would miss the whole point, but i've been thinking about installing one of those linux-only programs but give certain computers free access and make the vpn software run on their computers.
Thanks for your time anyway.

---

