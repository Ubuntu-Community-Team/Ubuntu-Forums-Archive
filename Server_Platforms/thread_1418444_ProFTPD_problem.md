---
title: "ProFTPD problem"
date: 2010-02-28
forum: Server Platforms
---

### Post by alecsmrekar on 2010-02-28
Hello,

I'm using Ubuntu 8.04 on my server. A couple days ago I saw that I couldn't download files from my server using FTP. The files are chmodded to 777, so that's not the problem. Alse chown is not the problem.

This is the user i'm using from /etc/proftpd/proftpd.conf:

<Anonymous /var/www>
User alecwww
Group ftp
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

I would really appreciate if you help me. 

Thank you, :)

Alec

---

