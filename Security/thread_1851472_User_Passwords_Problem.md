---
title: "User Passwords Problem"
date: 2011-09-28
forum: Security
---

### Post by swg1cor14 on 2011-09-28
I dont know what I did. I have Ubuntu Server 11 setup. I have apache2 and php and pureftp installed. Virtual hosts, with mysql, phpmyadmin...the whole 9 yards. 

Everything was working fine. Then we lost power. When the server came back online, I could access the web sites, SSH and mysql. But I could no longer FTP into system.

I purged pureftp and reinstalled. I tried changing passwords. I even created a new FTP user from the command line. My FileZilla FTP client reports this:

Response:    220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:    220-You are user number 1 of 50 allowed.
Response:    220-Local time is now 11:18. Server port: 21.
Response:    220-This is a private system - No anonymous login
Response:    220-IPv6 connections are also welcome on this server.
Response:    220 You will be disconnected after 15 minutes of inactivity.
Command:    USER joe
Response:    331 User joe OK. Password required
Command:    PASS ********
Response:    530 Login authentication failed
Error:    Critical error
Error:    Could not connect to server

Yeah I made a simple Joe account with a simple password just to see if I could get in. Root account doesnt log in (I know ur not supposed to use that but I tried it). My main user account sgauerke doesnt work. Even if I change the passwords to everything to 1234 it still wont work.

Its like its not decrypting the password to authenticate or something. Please help.

[EDIT] I tried VSFTPD as well. Same issue.

---

### Post by 2F4U on 2011-09-28
Am I right in assuming that it is still possible to login to the server locally and that any remote login fails?

---

### Post by swg1cor14 on 2011-09-28
> **2F4U said:**
> Am I right in assuming that it is still possible to login to the server locally and that any remote login fails?
via ssh yes. but ftp no. it seems only ftp is affected. but ive removed and installed both proftp and vsftp. no i didnt have them  both  running

---

### Post by collisionystm on 2011-09-28
how are you going about changing passwords? 
Are you using sudo passwd username

---

### Post by swg1cor14 on 2011-09-28
im not changing user passwords. but ftp user passwords.

---

### Post by collisionystm on 2011-09-28
I use Zentyal for my platform, I am not sure what FTP service it is using but the passwords are governed by the actual user password. I would try that just to test.

---

