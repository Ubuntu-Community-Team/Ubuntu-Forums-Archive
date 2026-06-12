---
title: "ftp server problems"
date: 2008-02-05
forum: Server Platforms
---

### Post by sflemi17 on 2008-02-05
Hey, I'm having a little trouble with setting up a ftp server. Everything works fine from inside my network, however, outside it does something strange, it displays the ftp message and prompts for a user, but on entring a user the connection is closed.

[PHP]
[00:37:54] SmartFTP v2.5.1008.33
[00:37:54] Resolving host name "80.195.217.43"
[00:37:54] Connecting to 80.195.217.43 Port: 21
[00:37:54] Connected to 80.195.217.43.
[00:38:04] 220 ProFTPD 1.2.10 Server (Debian) [80.195.217.43]
[00:38:04] USER web
[00:38:04] An established connection was aborted by the software in your host machine.
[00:38:04] Cannot login waiting to retry (30s)...
[00:38:04] Server closed connection
[/PHP]

I have shorewall firewall installed and ithas ports 21 and 20 open. Even more interesting is if i use the net2ftp website, i can connect to the server fine. 

Please help, this is drving me mad.

---

### Post by HermanAB on 2008-02-05
FTP uses more than just port 21.  Port 21 is used for the control channel, thereafter the data is transferred over a random high port.  You need to enable a FTP Tracker, for it to work through a firewall.

Anyhoo, FTP is insecure and sends your user name and password in plain text, so it is better to use SSH.

Cheers,

Herman

---

### Post by sflemi17 on 2008-02-06
I'm still a bit confused as to why it get disconnected when you send the user.I understand that port 21 is used for the control, which i thought was used for the sending the username and password.

 I have proftd configured to use passive in the port range 49152-50000.

My Shorewall Configuration
[PHP]
DNAT	net	fw:10.10.10.1	tcp	20
DNAT	net	fw:10.10.10.1	tcp	21
DNAT	net	fw:10.10.10.1 	tcp 	49152:50000
[/PHP]

---

### Post by freebeer on 2008-02-06
Try accessing it in ACTIVE mode and see if that makes any difference.  If it does, your PASSIVE mode is probably the issue.  Are you behind a router?  The router would need to have its ports opened too, I would imagine.

I was never able to get proftp to work in PASSIVE mode.  I suspect my router wasn't opening the ports properly (despite a rule) but that's really just speculation on my part... it all worked in ACTIVE mode, which is just fine for my needs, so I left it that way.

---

### Post by sflemi17 on 2008-02-06
Tried it is ACTIVE mode, no suck luck! Still not working! It actually creates the connection to the server, it's only when i enter the user that is closes the connection.

using windows built in ftp
[PHP]Connected to 80.195.217.43
220 ProFTPD 1.2.10 Server (Debain) [80.195.217.43]
User (80.195.217.43:(none)): webb
Connection closed by remote host.[/PHP]

---

### Post by sflemi17 on 2008-02-06
Turns out that there is nothing wrong with my setup, and the cause is something happening with port 21 on the ISP. I have changed it to another port and it is now working. :)

---

### Post by freebeer on 2008-02-06
I don't think I've ever used windows' ftp... I suspect that its default is PASSIVE mode (most ftp clients will default to passive mode once you're connected).  I think that's what's happening... once connected, the client and server switch (default behavior) to PASSIVE mode.  Unless you explicitly tell both to remain in ACTIVE mode.

---

### Post by freebeer on 2008-02-06
heh.. you posted while I was composing.  Yeah... it certainly looked like a port problem... I was just assuming it had to do with active vs passive modes. ;)

---

