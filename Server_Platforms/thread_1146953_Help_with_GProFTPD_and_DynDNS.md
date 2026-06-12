---
title: "Help with GProFTPD and DynDNS"
date: 2009-05-03
forum: Server Platforms
---

### Post by SickNick on 2009-05-03
Im trying to set up an FTP server for the first time and I am having trouble. So far I chose to use GProFTPD for now since it seems like the simplest solution. I have a Belkin N1 router which I set up my DDNS account to and it works. Now here are the steps I have taken to create a server, somewhere here I have had to have made an error.

1. I made a DynDNS account and I created a Host, which on this forum we will call "sicknick.homelinux.com", that is not what I used but lets refer to that.

2. In my Belkin N1, I went to Virtual Servers and added FTP Server, which has:

Inbound ports 21 through 21
Private Ports 21 through 21
Type = TCP
Private IP = 192.168.2.50

3. I went to DDNS in my Belkin N1 and I chose DynDNS as my DDNS Service, I entered my log in and gave it my host name which we said we would call sicknick.homelinux.com, and I successfully configured that.

4. I went to my wicd and under my current connection I went to advanced settings and did this

Use Static IPs = Check
Static IP = 192.168.2.50
Netmask = 255.255.255.0
Gateway = 192.168.2.1

And I used the openDNS servers that I have set up in my router as the DNS.

5. I open GProFTPD and I type in

Server = 192.168.2.50 or sicknick.homelinux.com (Tried both)
Server name = SickNick FTP
Server port = 21
NAT router = 192.168.2.1 ON or None OFF (Tried both)
Left the rest as the default
Activated the server



Now if I goto sicknick.homelinux.com, it takes me to my Belkin N1 page.

I tried using FireFTP to connect to

sicknick.homelinux.com port 21 as anonymous

192.168.2.50 port 21 as anonymous

Niether worked, what am I doing wrong, and shouldn't sicknick.homelinux.com be taking me to the ftp? I am totally new at this so please provide me with as much detail as possible to setting up every aspect of an FTP server from configuring my hardware to software. I also used [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to check if my port 21 is open, and it was open using my external IP. Please let me know what I should do to fix this problem :confused:

---

