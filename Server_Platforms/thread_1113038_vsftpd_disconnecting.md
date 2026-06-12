---
title: "vsftpd disconnecting"
date: 2009-04-01
forum: Server Platforms
---

### Post by shingalated on 2009-04-01
For some reason my Ubuntu Hardy (but with latest vsftpd) vsftpd ftp server disconnects users most of the time, but does seem to work randomly from time to time.  The client always is disconnected after entering passive mode, as shown in the vsftpd log file below.  The server is behind a Cisco ASA firewall, but ports 20-22 and 100-500 are opened for ftp.  Here is my vsftpd.conf file:
[http://pastebin.com/m5dda2e6f]("http://pastebin.com/m5dda2e6f")

Any help would be greatly appreciated, if this is not resolved the FTP server will be replaced by a windows server :'(

Log from VSFTPD:
```
Wed Apr  1 08:49:01 2009 [pid 23357] CONNECT: Client "172.21.2.101"
Wed Apr  1 08:49:01 2009 [pid 23357] FTP response: Client "172.21.2.101", "220 (
vsFTPd 2.0.6)"
Wed Apr  1 08:49:01 2009 [pid 23357] FTP command: Client "172.21.2.101", "USER s
ales"
Wed Apr  1 08:49:01 2009 [pid 23357] [sales] FTP response: Client "172.21.2.101"
, "331 Please specify the password."
Wed Apr  1 08:49:01 2009 [pid 23357] [sales] FTP command: Client "172.21.2.101",
 "PASS <password>"
Wed Apr  1 08:49:01 2009 [pid 23356] [sales] OK LOGIN: Client "172.21.2.101"
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP response: Client "172.21.2.101"
, "230 Login successful."
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP command: Client "172.21.2.101",
 "CWD /"
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP response: Client "172.21.2.101"
, "250 Directory successfully changed."
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP command: Client "172.21.2.101",
 "TYPE A"
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP response: Client "172.21.2.101"
, "200 Switching to ASCII mode."
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP command: Client "172.21.2.101",
 "PASV"
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP response: Client "172.21.2.101"
, "227 Entering Passive Mode (204,13,44,76,251,213)"
Wed Apr  1 08:49:01 2009 [pid 23358] [sales] FTP command: Client "172.21.2.101",
 "LIST"
Wed Apr  1 08:49:21 2009 [pid 23355] [sales] FTP response: Client "172.21.2.101"
, "425 Failed to establish connection."
Wed Apr  1 08:49:21 2009 [pid 23355] [sales] FTP command: Client "172.21.2.101",
 "QUIT"
Wed Apr  1 08:49:21 2009 [pid 23355] [sales] FTP response: Client "172.21.2.101"
, "221 Goodbye."

```

---

### Post by shingalated on 2009-04-02
Okay I found some sort of consistency, it usually seems to work okay when logging in Firefox...Why is it it gives a directory listing in Firefox but nothing else (Filezilla, CLI FTP, FireFTP, IE6?)

---

### Post by max_power on 2009-09-25
Im having the same problem. Did you find a cure?

---

### Post by John Cheng on 2009-09-25
What errors are you getting? The OP's log showed that the passive port was on 64469 (read [http://effbot.org/zone/asyncore-ftp-client.htm](http://effbot.org/zone/asyncore-ftp-client.htm) on how to understand response code 227). 

What are your passive ports? Do you have a firewall or system settings blocking those ports?

---

