---
title: "Need help with ftp connection"
date: 2012-07-19
forum: Server Platforms
---

### Post by karu309 on 2012-07-19
Hi there,


I am facing a problem with ftp connection. When i connect and put a file using ftp, the file transfers successfully. Here is list of commands and messages.

```
[root@localhost ~]# ftp 192.168.1.66
Connected to 192.168.1.66 (192.168.1.66).
220 qas FTP server (Version 4.2 Tue Oct 19 16:17:02 CDT 2010) ready.
Name (192.168.1.66:root): mastermahesh
331 Password required for mastermahesh.
Password:
230-Last unsuccessful login: Wed Jul 18 16:33:25 IST 2012 on ftp from ::ffff:192.168.102.1
230-Last login: Thu Jul 19 10:51:07 IST 2012 on ftp from ::ffff:192.168.102.1
230 User mastermahesh logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd masteroutput
250 CWD command successful.
ftp> put /home/admin/temp/test.txt test123.txt
local: /home/admin/temp/test.txt remote: test123.txt
***227 Entering Passive Mode (192,168,1,66,255,240)***
150 Opening data connection for test123.txt.
226 Transfer complete.
25 bytes sent in 0.00782 secs (3.20 Kbytes/sec)
ftp> ls -l
***227 Entering Passive Mode (192,168,1,66,128,243)***
150 Opening data connection for /bin/ls.
total 0
-rwxrwxrwx    1 mastermahesh    system         1490 May 19 17:48 20120519.txt
-rw-r-----    1 mastermahesh    system           25 Jul 19 10:53 test123.txt
226 Transfer complete.
ftp> 
```

The same thing i used to do with Spring Integration scheduler and i am getting following error


```
Caused by: org.springframework.integration.MessagingException: Failed to write to '/Test/output/MW01_0510_20120709.txt/MW01_0510_20120709.txt.writing' while uploading the file
	at org.springframework.integration.file.remote.handler.FileTransferringMessageHandler.sendFileToRemoteDirectory(FileTransferringMessageHandler.java:227)
	at org.springframework.integration.file.remote.handler.FileTransferringMessageHandler.handleMessageInternal(FileTransferringMessageHandler.java:136)
	... 36 more
Caused by: java.io.IOException: Failed to write to '/Test/output/MW01_0510_20120709.txt.writing'. Server replied with: 425      No data connection

	at org.springframework.integration.ftp.session.FtpSession.write(FtpSession.java:81)
	at org.springframework.integration.file.remote.handler.FileTransferringMessageHandler.sendFileToRemoteDirectory(FileTransferringMessageHandler.java:222)
	... 37 more
```


I have contacted spring integration forum and they found that it is OK with spring integration configuration. The problem is might be due to some ftp client or ftp server.

On searching, i found that it might be due to some active - passive ftp connection. As you can see in the above code, i have marked line bold+ italic effect.

Please suggest some solution.

Following are the referred links i have visited

[http://forum.springsource.org/showthread.php?128213-FTP-Connection-Problem]("http://forum.springsource.org/showthread.php?128213-FTP-Connection-Problem")

[http://slacksite.com/other/ftp.html]("http://slacksite.com/other/ftp.html")

[http://www.serverintellect.com/support/ftp/ftp-active-passive-diff.aspx]("http://www.serverintellect.com/support/ftp/ftp-active-passive-diff.aspx")

---

