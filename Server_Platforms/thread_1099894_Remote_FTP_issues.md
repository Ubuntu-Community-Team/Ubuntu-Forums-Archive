---
title: "Remote FTP issues"
date: 2009-03-18
forum: Server Platforms
---

### Post by perks on 2009-03-18
I'm trying to access my FTP server from a remote address. My server is set up to work with DynDns. When I try to connect with my FTP client it shows this:
```
Status:	Connecting to 67.81.64.58:10001...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.0.7)
Command:	USER james
Response:	331 Please specify the password.
Command:	PASS ********
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	 UTF8
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/home/james"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (192,168,1,150,225,100)
Status:	Server sent passive reply with unroutable address. Using server address instead.
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```
Why is it returning the local address where it says "Response: 227 Entering Passive Mode"? What can I do to fix this? All help is appreciated!

---

### Post by HermanAB on 2009-03-18
The FTP protocol is funny in that it reverses the connection once authenticated - the server becomes a client and the client becomes a server.  This shifts the bulk of the CRC calculations and other overhead to the client doing the download, which enables a FTP server to handle a large number of downloaders, because it doesn't have to do much.  

However, to do that it selects a random high port for the data connection.  So your firewall either needs to allow all ports (no firewall) or it needs a FTP connection tracker, otherwise the data connection will always die on you.

So, you may have better luck with SSH, since it only uses port 22.

Cheers,

Herman

---

### Post by perks on 2009-03-18
Thanks for the quick reply. I guess I'm stuck with SSH then. Thanks again.

---

