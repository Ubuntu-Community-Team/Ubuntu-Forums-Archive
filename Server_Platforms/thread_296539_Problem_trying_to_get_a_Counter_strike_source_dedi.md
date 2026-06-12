---
title: "Problem trying to get a Counter strike source dedicated server running"
date: 2006-11-09
forum: Server Platforms
---

### Post by sleeperknight on 2006-11-09
I've been trying to get a CS:S server running all day, I've got it installed correctly and everything, i have a few questions, Am i suppose to to lunch the srcds_run executable text file (won't load, only in the terminal), or am a suppose to open it up in the terminal? when i try to start a server i get some error that i cant connect to some port

patrick@patrick-desktop:~$ cd srcds
patrick@patrick-desktop:~/srcds$ ./srcds_run -game cstrike +maxplayers 20 +map de_dust +ip xxx.xxx.xxx.xxx (my ip right?) -port 27015 &
[1] 1518
patrick@patrick-desktop:~/srcds$ Auto detecting CPU
Using SSE2 Optimised binary.
Auto-restarting the server on crash

Console initialized.
Game.dll loaded for "Counter-Strike: Source"
maxplayers set to 32
maxplayers set to 20
WARNING: NNET_OpenSocket: bind: Cannot assign requested address
Couldn't allocate dedicated server UDP port
Add "-debug" to the ./srcds_run command line to generate a debug.log to help with solving this problem
Wed Nov 8 22:17:29 PST 2006: Server restart in 10 seconds

anyone know the problem?

---

### Post by benighted on 2007-02-23
well it looks as though the IP you're trying to use to host the server can't do it, it must be wrong. try using:

+port 27015

instead of -port 27015

yes, the linux server is terminal only, there's no gui for it (yet) unless I'm mistaken. 

oh and check if you have a firewall blocking the ports it needs, or if you have them forwarded to the right local IP address, if you're behind a router. 

I'm no wizard at getting it running, hell, I can't get it to let anyone join when I try to host it on my ubuntu server box, but thats just what I've learned in my quest to get it running myself.

---

### Post by Buddy The Cat on 2007-03-01
I was fooling around with SRCDS today on my box, and I found that the problem is with your +ip.  For some reason it gave me the same error on mine.  Just a guess, try taking it out of the command.

---

### Post by golfing22 on 2007-03-01
Yes, I'm running a counter strike source server on my server, and it's not necessary to use the +ip and +port commands unless you want it to change the port/ip it listens too.  By default it should work just fine though.

---

### Post by Icenate001 on 2008-06-17
i took it out and when i go to play or look for it in the server list I can not find it,when i go to look at what games are running in the lan tab it shows up there.. i put lan= 0 as well or what ever i know it is 0 in the cfg file. can anyone help

---

### Post by Lapp-Same on 2008-06-20
> **Icenate001 said:**
> i took it out and when i go to play or look for it in the server list I can not find it,when i go to look at what games are running in the lan tab it shows up there.. i put lan= 0 as well or what ever i know it is 0 in the cfg file. can anyone help

you are on the same LAN as the Server soo for you it would appear in LAN tab because you're both are on the same LAN, and for other people who are not, in the WAN/internet tab if you got a public-adress and a you're DMZ in the router pointet to the server!

---

