---
title: "proftpd: make a user"
date: 2014-04-20
forum: Server Platforms
---

### Post by hudic20 on 2014-04-20
Hello

I have **problem** with **gadmin-proftpd 0.4.2**.

When I make a user, cant login... why?

Port: 21 is open, ftp run on virtualbox (network NAT bridged)

Here is log from **Filezilla**:

Status:	Connecting to [myip]:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.4a Server (Debian) [::ffff:(myip)]
Command:	USER testuser
Response:	331 Password required for testuser
Command:	PASS ***************
[b]Response:	530 Login incorrect.
Error:	Critical error
Error:	Could not connect to server[/b]

Login incorrect, but i write password and all I need. :(

Tnx for help. :)

---

### Post by bapoumba on 2014-04-20
Moved to its own thread.

---

