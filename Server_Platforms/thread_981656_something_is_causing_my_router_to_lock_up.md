---
title: "something is causing my router to lock up"
date: 2008-11-13
forum: Server Platforms
---

### Post by specail on 2008-11-13
I have the most recent firmware available for the ol' linksys router. the server is ubuntu 2.6.27-7-server, I followed 'The perfect server' guide to set it up.

Every few days my connection will get sluggish, and go out intermittently, for all machines on the network. I have traced it back to the linux server i have hosting a basic website, and running bind9

the only thing i have found odd is a long list from ntop "last minute view" 
the list keeps changing with new ports.
TCP/UDP Port	Total	Sent	Rcvd
3000	3000	73.0 KBytes	27.2 KBytes	45.7 KBytes
54795	54795	1.9 KBytes	760	1.2 KBytes
54798	54798	1.9 KBytes	759	1.2 KBytes
54802	54802	1.9 KBytes	758	1.2 KBytes
54796	54796	1.9 KBytes	761	1.1 KBytes
54782	54782	1.9 KBytes	759	1.1 KBytes
54800	54800	1.8 KBytes	754	1.1 KBytes
54803	54803	1.8 KBytes	762	1.1 KBytes
54822	54822	1.1 KBytes	774	365
54838	54838	1.1 KBytes	773	365
54791	54791	1.1 KBytes	773	365
54811	54811	1.1 KBytes	772	365
54813	54813	1.1 KBytes	771	365
54799	54799	1.1 KBytes	771	365
54840	54840	1.1 KBytes	770	365
54830	54830	1.1 KBytes	770	365
54810	54810	1.1 KBytes	770	365
54787	54787	1.1 KBytes	770	365
54783	54783	1.1 KBytes	770	365
54828	54828	1.1 KBytes	769	365
54826	54826	1.1 KBytes	769	365
54816	54816	1.1 KBytes	769	365
54814	54814	1.1 KBytes	769	365
54797	54797	1.1 KBytes	769	365
54786	54786	1.1 KBytes	769	365
54836	54836	1.1 KBytes	768	365
54834	54834	1.1 KBytes	768	365
54825	54825	1.1 KBytes	768	365
54824	54824	1.1 KBytes	768	365
54818	54818	1.1 KBytes	768	365
54794	54794	1.1 KBytes	768	365
54793	54793	1.1 KBytes	768	365

I am rather new to linux/ubuntu, but it does seem like it is port scanning...

---

### Post by cariboo on 2008-11-13
What services are you running on your server and which ports do you have open on your router. You can do a quick scan using nmap. I've got a stock wrt54gs and I can scan my external ip address, you experience may differ. Your server just may be experiencing heavy loads, but it would be a good thing to check the logs.

Jim

---

### Post by iponeverything on 2008-11-13
is your server being being nat'ed by the linksys?  If it's not, it would not be a bad idea --

---

