---
title: "FTP Help Please - Absolute Beginner"
date: 2009-02-01
forum: Server Platforms
---

### Post by designcentral on 2009-02-01
Hi,

Need help configuring ProFTPD.

I have it installed however when I connect it says: 

Status:	Connecting to 192.168.1.107:21...
Status:	Connection established, waiting for welcome message...

It stays on that for about 10-15 seconds and then it says:

Response:	220 FTP Server ready.
Command:	USER bradley
Response:	331 Password required for bradley
Command:	PASS *******
Response:	230 User bradley logged in
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Status:	Directory listing successful

Also, when I click on a directory it takes around 10 seconds to load and when I finally upload a file it takes quite a while also.

This is the log when I upload a file. - It seems to re-connect before uploading!

Response:	150 Opening ASCII mode data connection for file list
Response:	226 Transfer complete
Status:	Directory listing successful
Status:	Connecting to 192.168.1.107:21...
Status:	Connection established, waiting for welcome message...
Response:	220 FTP Server ready.
Command:	USER bradley
Response:	331 Password required for bradley
Command:	PASS *******
Response:	230 User bradley logged in
Status:	Connected
Status:	Starting upload of C:\Users\Bradlet\Desktop\IMG_0251.JPG
Command:	CWD /public_html
Response:	250 CWD command successful
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (192,168,1,107,178,140).
Command:	STOR IMG_0251.JPG
Response:	150 Opening BINARY mode data connection for IMG_0251.JPG
Response:	226 Transfer complete
Status:	File transfer successful

Any help is much appreciated!

---

### Post by designcentral on 2009-02-01
I FIXED IT!

YAY

Just added 'UseReverseDNS off' to my conf file. All done I'm very very happy.

---

