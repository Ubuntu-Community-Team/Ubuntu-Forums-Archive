---
title: "pure-ftpd server: Windows clients can't connect"
date: 2010-07-20
forum: Server Platforms
---

### Post by ader10 on 2010-07-20
I am setting up an ftp server with pure-ftpd.
I followed this guide:
[http://www.ubuntu-howto.info/howto/how-to-install-and-configure-pure-ftpd](http://www.ubuntu-howto.info/howto/how-to-install-and-configure-pure-ftpd)
but where the guide uses /bin/null I used /dev/null

I can log in on both linux and windows clients, but windows clients can't retrieve a directory listing.
Screenshots illustrating my problem are attached to this post.

```
Status:	Connecting to 192.168.1.99:21...
Status:	Connection established, waiting for welcome message...
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 2 of 20 allowed.
Response:	220-Local time is now 21:55. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER administrator
Response:	331 User administrator OK. Password required
Command:	PASS 
Response:	230-User administrator has group access to:  2001      
Response:	230 OK. Current directory is /
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (96,255,184,117,198,255)
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

Please help me solve this problem.

---

