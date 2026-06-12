---
title: "Pure-FTP login error"
date: 2012-04-22
forum: Server Platforms
---

### Post by siXor on 2012-04-22
I've installed Pure-FTPd and am trying to get virtual users to work with it. Unix users are OK and are able to transfer files but my virtual user that I created can't log in.
I'm running Linux Ubuntu Server 10.04 x64 and this is what I've done:
sudo apt-get install pure-ftpd
changed to standalone in /etc/default/pure-ftpd-common
/etc/pure-ftpd/conf/PassivePortRange: 5560 5580
/etc/pure-ftpd/conf/UnixAuthentication: yes
sudo pure-pw useradd test -u ftpuser -d /users/testuser
/etc/init.d/pure-ftpd restart
Then I connected to the user test on the FTP-server.
Status: Looking up adress for domain 
Status: Connecting to xxx.xxx.xxx.xxx:21... 
Status: Connection established, waiting for welcoming message... 
Answer: 220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Answer: 220-You are user number 1 of 10 allowed. 
Answer: 220-Local time is now 21:57. Server port: 21. 
Answer: 220-This is a private system - No anonymous login 
Answer: 220-IPv6 connections are also welcome on this server. 
Answer: 220 You will be disconnected after 15 minutes of inactivity. 
Command: USER evasion Answer: 331 User evasion OK. Password required 
Command: PASS*** 
Answer: 530 Login authentication failed 
Error: Critical error 
Error: Could not connect to server


I know that my password is correct since I've retyped 5 times allready and only contains three numbers.
So what have I done wrong? Maybe it's something with the .pdb-file? but since the user exists in the passwd for pure-ftpd I figured that shouldn't be the problem. I'm most thankful for all the help I can get.

---

### Post by siXor on 2012-04-22
Never mind. Found the solution now after a few hours searching. 

sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure

I think it's strange that people does not mension this in their tutorials and how-to:s. Anyhow, problem solved!

---

