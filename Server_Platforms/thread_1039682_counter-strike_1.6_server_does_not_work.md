---
title: "counter-strike 1.6 server does not work"
date: 2009-01-14
forum: Server Platforms
---

### Post by Mykle87 on 2009-01-14
I installed Ubuntu Server Edition 8.10 and installed CS 1.6 using this [guide]("http://www.cstrike-planet.com/tutorial/1/6"). I start up the server and I am able to connect to it on my lan. I tried forwarding the ports but when that didn't work I just put the computer in a DMZ. Here is the server output:

```
michael@ubuntu:~/hlds$ sudo ./hlds_run -game cstrike -autoupdate +maxplayers 20 +map de_aztec
Auto detecting CPU
Using AMD Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Counter-Strike Base Content' version 25


Checking/Installing 'Linux Server Engine' version 42


Checking/Installing 'Half-Life Base Content' version 12


HLDS installation up to date

Console initialized.
scandir failed:/home/michael/hlds/./valve/SAVE
scandir failed:/home/michael/hlds/./platform/SAVE
Protocol version 48
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 18:01:18 Oct 24 2008 (4352)
STEAM Auth Server
couldn't exec language.cfg
Server IP address XXXXXXXXXXXXXXXXXX:27015 (**internal lan ip here**)
scandir failed:/home/michael/hlds/./valve/SAVE
scandir failed:/home/michael/hlds/./platform/SAVE
[S_API FAIL] SteamAPI_Init() failed; unable to update local steamclient. Continuing with current version anyway.

couldn't exec listip.cfg
couldn't exec banned.cfg
Adding master server 69.28.151.162:27010
Adding master server 72.165.61.189:27010
Connection to Steam servers successful.
   VAC secure mode is activated.

```

Everything looks fine to me. I can join no problem but nobody can join when I give them my external ip. Also, I installed LAMP and when people put my external ip address in Firefox, the default page loads no problem. So I feel like that is a good sign right? Any help is appreciated thanks.

---

### Post by Mykle87 on 2009-01-15
I changed the port of the server to 80 (which is probably a terrible idea) to see if it would work because I know that port is not blocked. Still no change. My ISP is Comcast. Could that have something to do with it? Please help me figure this out.

---

### Post by cariboo on 2009-01-15
Try [canyouseeme]("http://www.canyouseeme.org/") to see if the ports you have open can be seen from the intenet.

Jim

---

### Post by Mykle87 on 2009-01-15
Thanks for the neat little website. Here is what I don't understand though, I typed in port 27015, 80, 22, and 3389. All of them came back with errors. However, my apache2 website can be viewed by my friends. What does this mean? Websites run on port 80 right?

---

### Post by Mykle87 on 2009-01-15
I just realized that I am doing this on my vista machine. I guess I have to run this website on my ubuntu server? I don't have a gui on it. What do you suggest I do?

---

### Post by Mykle87 on 2009-01-15
Ok this is what I just did on my vista machine:
1. Add port 27015 to vista firewall
2. Port forward 27015 on router to vista machine
3. Used website to check port 27015 and it timed out
In conclusion, comcast blocks that port and just about every other port? If so, I hate comcast. I wonder if this would work on my friend's fios connection.

---

