---
title: "atftpd - How to make it work,"
date: 2006-06-30
forum: Server Platforms
---

### Post by eentonig on 2006-06-30
Hi,

I've got some problems with my tftp server. I've got it started, but I can't copy any file from or to the server.

The file exists:
```
-rwxrwxrwx  1 rfonteyn rfonteyn    0 2006-06-30 11:31 config.txt
```

The tftpboot directory exists
```
rfonteyn@RFONTE-FCS:/$ ll | grep tft
drwxrwxrwx   2 root     root     4.0K 2006-06-30 11:33 tftpboot/
```

In var/log/syslog I see that the request is received and serverd(?)
```
Jun 30 13:31:55 localhost atftpd[10592]: Advanced Trivial FTP server started (0.7)
Jun 30 13:31:55 localhost atftpd[10592]: Serving config.txt to 10.1.7.249:55305
Jun 30 13:36:55 localhost atftpd[10592]: atftpd terminating after 300 seconds
Jun 30 13:36:55 localhost atftpd[10592]: Main thread exiting

```

But on the other side (Cisco switch) I've get following error
```
switch#copy tftp: sup-bootflash:
Address or name of remote host []? 10.1.4.9
Source filename []? config.txt
Destination filename [config.txt]?
Accessing tftp://10.1.4.9/config.txt...
%Error opening tftp://10.1.4.9/config.txt (No such file or directory)
```

Does anybody got an idea to what is going wrong?

[http://ubuntuforums.org/showthread.php?t=47026&highlight=atftpd](http://ubuntuforums.org/showthread.php?t=47026&highlight=atftpd)

---

### Post by fnjordy on 2006-07-02
Possibly a MTU problem?  ATFTPD seems to have closed the connection due to timeout and the client never received anything.  Does it work localhost?

---

