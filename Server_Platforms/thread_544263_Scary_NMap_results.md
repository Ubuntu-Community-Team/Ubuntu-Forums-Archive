---
title: "Scary NMap results?"
date: 2007-09-06
forum: Server Platforms
---

### Post by dynamethod on 2007-09-06
Hey there ive recently made the jump from winXP to Ubuntu, loving Ubuntu :)

well thing is im on a LAN(wired), and i share this LAN with 3 others(who all run windowsXP) and i recently installed Nmap and done a scan from 192.168.1.0-255

the routers address is 192.168.1.254 btw, the router is a billion bipac 7200, the firewall option is enabled.

this is the result of the NMap scan:

All 1697 scanned ports on 192.168.1.243 are closed

Interesting ports on 192.168.1.254:
Not shown: 1690 closed ports
PORT      STATE    SERVICE
21/tcp    open     ftp
80/tcp    open     http
1999/tcp  filtered tcp-id-port
12345/tcp filtered NetBus
12346/tcp filtered NetBus
31337/tcp filtered Elite
54320/tcp filtered bo2k

Nmap finished: 256 IP addresses (2 hosts up) scanned in 15.661 seconds


Is the result saying that the Router is filtering the NetBus, Elite and bo2k attacks? or is it saying that these RAT's have infiltrated and infected the LAN?

feed back much appreciated :S

---

### Post by Seisen on 2007-09-06
According to nmap when a port comes up filtered it can not tell if the port is open or not because of packet filtering. Since it was your router that came up I would check out the settings on your router and any logs that your router might have.

---

### Post by speedup on 2007-09-06
I think made a mistake your doing a Nmap on the LAN side. The firewall of the router doesn't work on the LAN side. You may ask a person on the Internet to do an Nmap to your public IP and see if they will see any open ports.

---

### Post by dynamethod on 2007-09-06
heres my security log file from my router:

2007/09/06 10:43:02      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:49042 Dest IP:192.168.1.254   Port:12345

2007/09/06 10:43:02      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:40812 Dest IP:192.168.1.254   Port:119  

2007/09/06 10:43:02      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:55214 Dest IP:192.168.1.254   Port:12346

2007/09/06 10:43:03      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:49144 Dest IP:192.168.1.254   Port:12345

2007/09/06 10:43:03      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:55261 Dest IP:192.168.1.254   Port:12346

2007/09/06 10:52:26      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:56775 Dest IP:192.168.1.254   Port:899  

2007/09/06 10:52:26      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:57614 Dest IP:192.168.1.254   Port:654  

2007/09/06 10:52:27      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:46696 Dest IP:192.168.1.254   Port:1513 

2007/09/06 10:52:27      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:40509 Dest IP:192.168.1.254   Port:8080 

2007/09/06 10:52:28      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:48522 Dest IP:192.168.1.254   Port:6144 

2007/09/06 10:52:28      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:35440 Dest IP:192.168.1.254   Port:679  

2007/09/06 10:52:29      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:48563 Dest IP:192.168.1.254   Port:321  

2007/09/06 10:52:29      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:38721 Dest IP:192.168.1.254   Port:54320

2007/09/06 10:52:29      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:37809 Dest IP:192.168.1.254   Port:495  

2007/09/06 10:52:29      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:47159 Dest IP:192.168.1.254   Port:12345

2007/09/06 10:52:29      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:51776 Dest IP:192.168.1.254   Port:12346

2007/09/06 10:52:29      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:38878 Dest IP:192.168.1.254   Port:54320

2007/09/06 10:52:29      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:36794 Dest IP:192.168.1.254   Port:357  

2007/09/06 10:52:29      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:47318 Dest IP:192.168.1.254   Port:12345

2007/09/06 10:52:29      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:58111 Dest IP:192.168.1.254   Port:284  

2007/09/06 10:52:29      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:51927 Dest IP:192.168.1.254   Port:12346

2007/09/06 10:52:29      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:39041 Dest IP:192.168.1.254   Port:54320

2007/09/06 10:52:29      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:45231 Dest IP:192.168.1.254   Port:6667 

2007/09/06 10:52:29      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:47475 Dest IP:192.168.1.254   Port:12345

2007/09/06 10:52:29      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:52088 Dest IP:192.168.1.254   Port:12346

2007/09/06 10:52:29      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:55073 Dest IP:192.168.1.254   Port:17300

2007/09/06 10:52:30      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:52119 Dest IP:192.168.1.254   Port:12346

2007/09/06 10:52:30      Net Bus Scan        <TCP>  Source IP:192.168.1.243   Port:47564 Dest IP:192.168.1.254   Port:12345

2007/09/06 10:52:30      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:39203 Dest IP:192.168.1.254   Port:54320

2007/09/06 10:52:30      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:47888 Dest IP:192.168.1.254   Port:601  

2007/09/06 10:52:30      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:49881 Dest IP:192.168.1.254   Port:1999 

2007/09/06 10:52:30      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:39176 Dest IP:192.168.1.254   Port:31337

2007/09/06 10:52:30      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:56494 Dest IP:192.168.1.254   Port:18   

2007/09/06 10:52:30      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:50042 Dest IP:192.168.1.254   Port:1999 

2007/09/06 10:52:30      Back Orifice Scan   <UDP>  Source IP:192.168.1.243   Port:39333 Dest IP:192.168.1.254   Port:31337

2007/09/06 10:52:30      TCP SYN Flooding    <TCP>  Source IP:192.168.1.243   Port:41495 Dest IP:192.168.1.254   Port:911  

2007/09/06 10:52:30      Back Orifice Scan   <UDP>  Source IP:192.168.1.243   Port:39386 Dest IP:192.168.1.254   Port:31337

2007/09/06 10:52:30      Back Orifice Scan   <UDP>  Source IP:192.168.1.243   Port:39387 Dest IP:192.168.1.254   Port:31337

2007/09/06 10:52:31      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:50130 Dest IP:192.168.1.254   Port:1999 

2007/09/06 10:52:31      Trojan Scan         <TCP>  Source IP:192.168.1.243   Port:50131 Dest IP:192.168.1.254   Port:1999 

2007/09/06 11:08:14      Trojan Scan         <TCP>  Source IP:207.46.216.59   Port:80    Dest IP:58.28.153.202   Port:1243 

2007/09/06 11:08:16      Trojan Scan         <TCP>  Source IP:207.46.216.59   Port:80    Dest IP:58.28.153.202   Port:1243 

2007/09/06 11:08:23      Trojan Scan         <TCP>  Source IP:207.46.216.59   Port:80    Dest IP:58.28.153.202   Port:1243 

2007/09/06 11:10:24      Trojan Scan         <TCP>  Source IP:207.46.216.59   Port:80    Dest IP:58.28.153.202   Port:1243 

2007/09/06 12:58:16      TCP SYN Flooding    <TCP>  Source IP:85.190.0.3      Port:38388 Dest IP:58.28.153.202   Port:58   

2007/09/06 13:13:29      Trojan Scan         <TCP>  Source IP:127.0.0.1       Port:25    Dest IP:127.0.0.1       Port:1243 

2007/09/06 13:13:34      Trojan Scan         <TCP>  Source IP:127.0.0.1       Port:25    Dest IP:127.0.0.1       Port:1243 

2007/09/06 13:13:58      Trojan Scan         <TCP>  Source IP:127.0.0.1       Port:25    Dest IP:127.0.0.1       Port:1243 

2007/09/06 13:38:42      TCP SYN Flooding    <TCP>  Source IP:85.190.0.3      Port:42392 Dest IP:58.28.153.202   Port:58   

2007/09/06 14:25:40      TCP SYN Flooding    <TCP>  Source IP:85.190.0.3      Port:32840 Dest IP:58.28.153.202   Port:6000 


i still dont understand it much though
my LAN address is 192.168.1.243, which appears to be the "source IP" wth???

---

### Post by twistedtwig on 2007-09-06
I agree NMAP your router from the public side (number of free online sites that do it for you).. if you want to check the XP boxes are not all dirty with virues then I would do their IP's on their own (assuming there are not many machines).

Your router will probably show ports on things from the inside that are not avaiable on the outside.

for example when I namp my server it shows 6881 open lan side for torrent program and 80, 22 and 5900, but only 80 is open net side of things.

---

### Post by James79 on 2007-09-07
Using nmap from inside your network to test your router using its private IP isn't terribly useful. You might notice that you'll get different results depending on wether you scan your local ip (192.168.1.x) and your public ip. Try it and you'll see.

In your case, you can see you have port 80 opened, but that's for web administration. When you use firefox to connect to your router to change its configuration - it has a mini-webserver for that purpose, and that's what nmap is seeing. It doesn't mean it's accessible from the outside (in fact it probably isn't) unless you implicitly told it to do so)

Note that nmap is *not* a tool to determine which ports are opened, it determines *which ports are open AND have a server listening*. You could very well have a port open, but if no corresponding server isn't listening and accepting requests for that port nmap won't list it.

I hope that makes sense :)

---

### Post by steve.horsley on 2007-09-08
> Note that nmap is not a tool to determine which ports are opened, it determines which ports are open AND have a server listening. You could very well have a port open, but if no corresponding server isn't listening and accepting requests for that port nmap won't list it.

I hope that makes sense

From an operating system perspective, ports cannot be open **unless** there is a server process listening. If there is no server listening then the port will be "closed" - the OS will reply Port Unreachable to any attempt to talk to it. 

From a firewall perspective, "open" ports are those ports that the firewall allows packets through to. These ports may be either open or closed from an OS perspective of course, depending on whether they have been opened by a service process. Either way, nmap will call then filtered because it can't get a response to see whether they're really open or closed.

Don't confuse the two different meanings of the word open:
    opened on the OS by a server process, and
    open packet passage granted by the firewall



I'm a little concerned to see the router has port 21 (FTP) open. I can't think of a good reason why that should be, on a router.

---

