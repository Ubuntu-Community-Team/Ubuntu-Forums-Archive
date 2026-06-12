---
title: "pure-ftpd head aches connection timeouts"
date: 2011-09-25
forum: Server Platforms
---

### Post by Tavorisch on 2011-09-25
Hello all!

I have a perfect server with ISP config 3 for hosting websites for friends/family members but pure-ftpd is giving me some trouble.

24.119.186.239 is my external IP and my local subnet is 10.0.1.0 and my server is statically assigned to 10.0.1.25

I read some things that it might be the passive port so I forwarded 50,000-60,000 TCP and UDP and also port forwarded 21 TCP UDP obviously and 20 TCP UDP as well.. Locally it connects instantly and never fails, I've also ruled out DNS because it hangs when I use 24.119.186.239 or one of the few domain names. (also have tried it from work and other various locations)

The weird thing is that, if i try again it will usually work fine, sometimes it doesn't happen at all and sometimes it takes a few tries to get a directory listing.

This happens in filezilla/cuteftp/fireftp any help is much appreciated!!!

```
Status:	Resolving address of jump-jets.com
Status:	Connecting to 24.119.186.239:21...
Status:	Connection established, waiting for welcome message...
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 2 of 50 allowed.
Response:	220-Local time is now 03:17. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER jumpjetsftp
Response:	331 User jumpjetsftp OK. Password required
Command:	PASS ***********
Response:	230-User jumpjetsftp has group access to:  client6  sshusers
Response:	230 OK. Current restricted directory is /
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Extensions supported:
Response:	 EPRT
Response:	 IDLE
Response:	 MDTM
Response:	 SIZE
Response:	 REST STREAM
Response:	 MLST type*;size*;sizd*;modify*;UNIX.mode*;UNIX.uid*;UNIX.gid*;unique*;
Response:	 MLSD
Response:	 ESTP
Response:	 PASV
Response:	 EPSV
Response:	 SPSV
Response:	 ESTA
Response:	 AUTH TLS
Response:	 PBSZ
Response:	 PROT
Response:	 UTF8
Response:	211 End.
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PORT 10,0,1,10,207,66
Response:	500 I won't open a connection to 24.119.186.239 (only to 10.0.1.1)
Command:	PASV
Response:	227 Entering Passive Mode (24,119,186,239,219,66)
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

---

### Post by Tavorisch on 2011-09-25
Hm.. weird, it can't open connection to outside ip (only to local default gateway(router)

here is my 3rd try just now where I got a directory listing

```
Status:	Connecting to 24.119.186.239:21...
Status:	Connection established, waiting for welcome message...
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 3 of 50 allowed.
Response:	220-Local time is now 03:32. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER patrickjared
Response:	331 User patrickjared OK. Password required
Command:	PASS ***********
Response:	230-User patrickjared has group access to:  client5  sshusers
Response:	230 OK. Current restricted directory is /
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (24,119,186,239,236,162)
Command:	MLSD
Response:	150 Accepted data connection
Response:	226-ASCII
Response:	226-Options: -a -l 
Response:	226 10 matches total
Status:	Directory listing successful
```

---

### Post by Tavorisch on 2011-09-25
Also,

This kind of stuff was happening BEFORE I forwarded 20 or 50,000-60,000.... didn't seem to make a difference.. Still would be able to login sometimes right away or after the 2nd or 3rd try.

---

### Post by lisati on 2011-09-25
The good news is that your system is accessible from the outside using gFTP, and since I don't have a valid user id/password to your system, that's as far as I got. Have a look at your system logs and you should see some failed login attempts from outside.

---

### Post by Tavorisch on 2011-09-26
bummer I haven't a clue on how to do that. I'll do some research tomorrow. I was hoping it was a simple port forward or listening setting in the pureftpd conf..

---

