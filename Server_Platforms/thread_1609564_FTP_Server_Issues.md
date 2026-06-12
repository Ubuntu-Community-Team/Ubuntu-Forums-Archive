---
title: "FTP Server Issues"
date: 2010-10-30
forum: Server Platforms
---

### Post by Glencore on 2010-10-30
Hello,

I am trying to set up an FTP server for my Joomla install. I followed the following guide I found:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

however I cannot get the joomla install to login. I used root and my password, host as 127.0.0.1 and the port as 21. 

Any help?

edit: I used my non-root account and now it does not say "cannot log in" it says "cannot retrieve a directory listing from the ftp server"

---

### Post by dapperdanny77 on 2010-10-30
127.0.0.1 is localhost - do you want to install joomla on the machine your are currently logged in?

your situation is not totally clear to me - please specify on which server joomla is going to run - if you want to install joomla on your desktop pc you don't need a ftp server. You can just copy the files.

you need a running LAMP installation - check out [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

you should fully understand your installation before connection your server to the internet

---

### Post by Glencore on 2010-10-30
> **dapperdanny77 said:**
> 127.0.0.1 is localhost - do you want to install joomla on the machine your are currently logged in?

your situation is not totally clear to me - please specify on which server joomla is going to run - if you want to install joomla on your desktop pc you don't need a ftp server. You can just copy the files.

you need a running LAMP installation - check out [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

you should fully understand your installation before connection your server to the internet

At the moment this is just a test server. It will be deployed at work and managed remotely, one I know I can get it to work fully. this is mine and the companies first venture into open source so I'm making sure I can deliver before I promise them all this awesumness for free.

The server is working great so far, it is serving the joomla install and I have gone through the first few steps. I want people to be able to transfer files to it remotely as we have a few offices with varying setups. 

The OS will be ubuntu server 10.04 LTS.

---

### Post by dapperdanny77 on 2010-10-30
ok - which ftp server software do you run (vsftp, proftpd ??)

the following command should bring the information
> 
dpkg -l | grep ftp 
lsof -i :21 #shows which process is listening on port 21 


basically your unprivileged user needs the proper file/directory permissions to access your files there (afaik the default configurations of the different ftp servers don't do special limitations)

---

### Post by Glencore on 2010-10-30
dpkg returns:
ftp 0.17-19biuld1 
vsftpd 2.2.2-3ubuntu6

lsof returns:

vsftpd 7715 root 3u IPv4 20826 0t0 TCP *:ftp (LISTEN)

when i run this command:

ftp localhost

I can log into the ftp but running ls does not return anything (other than directory listing done blah blah)

sorry I cannot copy and paste.

So I guess its something to do with directory permissions like u said.

is there anyway I can point it to /var/www/joomla and give a user permission to view it?

---

### Post by Glencore on 2010-10-30
I downloaded FileZilla on my Windows machine and was able to log in but the fiolder is empty but i could create a folder, so im guessing I need to change some default folder setting.

```
 
Status:	Connecting to 192.168.1.6:21...
Status:	Connection established, waiting for welcome message...
Response:	220 Welcome to the core-web FTP service.
Command:	USER glen
Response:	331 Please specify the password.
Command:	PASS *******
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
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (192,168,1,6,185,181).
Command:	LIST
Response:	150 Here comes the directory listing.
Response:	226 Directory send OK.
Status:	Directory listing successful
Status:	Retrieving directory listing...
Command:	CDUP
Response:	250 Directory successfully changed.
Command:	PWD
Response:	257 "/"
Status:	Directory listing successful
Status:	Creating directory '/New directory'...
Command:	MKD New directory
Response:	257 "/New directory" created

```

---

### Post by Glencore on 2010-10-30
Okay problem solved:


I added the line local_root = /var/www/joomla to the config file 

I added the user to the group www-data (the group that owns the folder)

I changed the permissions from 755 to 775 

Seems to work fine now.

---

### Post by dapperdanny77 on 2010-10-31
finally you made it !

---

