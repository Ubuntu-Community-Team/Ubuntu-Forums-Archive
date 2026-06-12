---
title: "FTP Daemon Problems"
date: 2009-08-01
forum: Server Platforms
---

### Post by tobiness on 2009-08-01
[B]Hey, I Am Currently Running Ubuntu 8.10 
I Used To Run SuSE On My Servers And Ran Apache, Bind DNS, MySQL, Php, And ProFTP[/B]D
However,
With ProFTPD On Ubuntu I Have Configured It To Allow Root Logins, And Logins From My Other User, However I Login Through A Shell Prompt And Get The Following:
Ftp
ftp>open
(to) 192.168.0.4
ftp: Connection Refused.

Before I was Getting
ftp
Ftp>open
(to) 192.168.0.4
Connection Accepted, Debian OS 
--------------PROFTPD-------------
Username: Root/User(Depends I tried both my users)
Password: **************************
Succesful Login, Welcome To Localhost
But Then When I tryed to get a directory Listing
ftp>Dir
PLEASE ENTER USER AND PASS
then i go
Ftp>Open (To test If Im Connected)
Please Disconnect From Localhost First!
What do i do? Get a different ftp server? What r some other good ones that will work on ubuntu? Etc,
Otherwise? How Can I Fix This! XD

---

### Post by tobiness on 2009-08-02
Ive tried heaps to get it going but no luck plz, som1 tell me a good ftpd!

---

### Post by nix4me on 2009-08-02
open is a command used to connect to another server.  Thats why it tells you to disconnect first.

Use the command ls to get a directory listing.

---

