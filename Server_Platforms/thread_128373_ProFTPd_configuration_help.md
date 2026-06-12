---
title: "ProFTPd configuration help"
date: 2006-02-11
forum: Server Platforms
---

### Post by t0bb3 on 2006-02-11
Hi

For the last few days I've been trying to get ProFTPd running on my computer. I'm at the point now that it works like it should in my local network, but it doesn't work quite like I want it when connecting from the outside.

Thing is that I can't get passive working when connecting from the outside. Both active and passive works like it should from inside my network, and active works from the outside. But as I said, passive doesn't work from the outside.

When I try to connect from over the internet I get the following messages:```
ftp> open xxxxx.gotdns.com nnnn
Connected to xxxxx.gotdns.com.
220 ProFTPD 1.2.10 Server (xxxxx's ftp) [83.88.205.nnn]
Name (xxxxx.gotdns.com:xxxxx): xxxxx
331 Password required for xxxxx.
Password:
230 User xxxxx logged in.
ftp> ls
200 PORT command successful
425 Unable to build data connection: Connection timed out
ftp>
```

I've got the following settings in my proftpd.conf that has to do with passive connections:```
MasqueradeAddress               xxxxx.gotdns.com
#this is a range, not just two ports:
PassivePorts                    6000 6100
UseReverseDNS                   off
IdentLookups                    off
AllowForeignAddress             on
```

Ports 6000 to 6100 are forwarded in my router's configuration

Thanks
//t0bb3

---

### Post by t0bb3 on 2006-02-18
This is the most verbose error message I've gotten:```
Status:	Connecting to 192.168.0.nnn ...
Status:	Connected with 192.168.0.nnn. Waiting for welcome message...
Response:	220 ProFTPD 1.2.10 Server (xxxxx's ftp) [80.166.180.nnn]
Command:	USER xxxxx
Response:	331 Password required for xxxxx.
Command:	PASS *********
Response:	230 User xxxxx logged in.
Command:	FEAT
Response:	211-Features:
Response:	211-MDTM
Response:	211-REST STREAM
Response:	211-SIZE
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (80,166,180,nnn,23,194).
Command:	LIST
Error:	Transfer channel can't be opened. Reason: No connection could be made because the target machine actively refused it.
Error:	Could not retrieve directory listing
```
Anyone know what it means?

I get this error when connecting from a machine running in VMWare on a computer in my local network

---

