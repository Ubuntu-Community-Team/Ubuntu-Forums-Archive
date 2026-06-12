---
title: "Connection to Pure-FTPd lost on USER command."
date: 2009-11-09
forum: Server Platforms
---

### Post by dip_10 on 2009-11-09
I can connect a remote pure-ftpd I can connect it. But once I try to login by user command, the connection is lost. The same thing happens with all FTP clients. 

```
Status:   Connecting to xxx.xxx.xxx.xxx:21...
Status:   Connection established, waiting for welcome message...
Response:   220---------- Welcome to Pure-FTPd [TLS] ----------
Response:   220-You are user number 4 of 200 allowed.
Response:   220-Local time is now 19:55. Server port: 21.
Response:   220-This is a private system - No anonymous login
Response:   220-IPv6 connections are also welcome on this server.
Response:   220 You will be disconnected after 15 minutes of inactivity.
Command:   USER ABCDEFGHIJ
Error:   Could not connect to server
Status:   Waiting to retry...
```

I cant understand whether it is a server problem or something from my workstation end which disconnects the already established connection once the USER command is entered. Please help.
Thank you.
Deep.

---

