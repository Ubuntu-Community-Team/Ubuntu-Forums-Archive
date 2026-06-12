---
title: "FTP Server setup to /var/www with current user"
date: 2008-06-01
forum: Server Platforms
---

### Post by xodeus on 2008-06-01
Hi.
How do I do that.
I want a ftp server running, which loads the /var/www when I'm logging in with my normal user account. 
which server and how to configure.
I want access to all operations with this user account. chmod and upload.

---

### Post by squirrel_chaser on 2008-06-01
I am not sure that I understand the entire question.  At work, I admin a Centos server running vsftp and you can configure the daemon to put the ftp files in any directory and allow or restrict the commands performed by the users.  

I'm not sure that answers you.

---

### Post by xodeus on 2008-06-02
I'll split my question up...

1. Which server is the easiest to administer?
proftpd, vsftpd or another one?

2. How do I set a user up on it pointing the user to /var/www with "root" access; read, write, chmod and so...

---

### Post by xodeus on 2008-06-03
I got it working with proftpd and gproftpd

---

### Post by Strychnine45 on 2008-06-04
I also cant seem to get ftp to work with filezilla. No matter what I try I cant connect to the server with filezilla using ftp and port 21 and username/pw.

Anyone share how they were able to set this up? I want to use FTP and filezilla to upload site files and chmod permissions

---

### Post by adamos on 2008-06-04
try host: ftp.urserver.com
user: [email]user@urserver.com[/email]
port 21 and give it a try

---

### Post by chuck jessup on 2008-07-15
nope not with filezilla

---

### Post by chuck jessup on 2008-07-15
"Status:	Connecting to [www.destructionreborn.com](www.destructionreborn.com) ...
Trace:	FtpControlSocket.cpp(938*'+'*): OnConnect(0)  OpMode=1 OpState=-1   caller=0x003edce4
Status:	Connected with [www.destructionreborn.com](www.destructionreborn.com). Waiting for welcome message...
Trace:	FtpControlSocket.cpp(761): OnReceive(0)  OpMode=1 OpState=-1   caller=0x003edce4
Response:	220 Ftp server ready.
Command:	USER [email]jesse@destructionreborn.com[/email]
Trace:	FtpControlSocket.cpp(761): OnReceive(0)  OpMode=1 OpState=0   caller=0x003edce4
Response:	331 User [email]jesse@destructionreborn.com[/email] okay, need password.
Command:	PASS ********
Trace:	FtpControlSocket.cpp(761): OnReceive(0)  OpMode=1 OpState=3   caller=0x003edce4
Response:	530 Login incorrect.
Trace:	FtpControlSocket.cpp(1077): DoClose(8196)  OpMode=1 OpState=3   caller=0x003edce4
Trace:	FtpControlSocket.cpp(3918*'+'*): ResetOperation(12292)  OpMode=1 OpState=3   caller=0x003edce4
Error:	Unable to connect!"

^^^ the closest i can get to connecting...

jesse fender

---

### Post by windependence on 2008-07-16
I really don't see why you don't just use ssh and WinSCP to do all this stuff. No need to install anything. No ftp server to run. Root access (if you have it enabled) or user access. On a Linux client you can use sftp through nautilus or Konqueror.

-Tim

---

### Post by nanog on 2008-07-17
Because generic web browsers handle ftp and computer phobic types will never install an ssh/sftp client.

---

### Post by windependence on 2008-07-17
> **nanog said:**
> Because generic web browsers handle ftp and computer phobic types will never install an ssh/sftp client.

He didn't give me the impression he was giving access to anyone but himself. For "users" I understand this but for him to upload stuff to his own web server, it's not necessary. In his OP, he mentions chmod, and other things. I don't think he wants everyone to have that access....unless you were saying HE is computer phobic, which I doubt. :)

-Tim

---

