---
title: "ProFTPd - Can't set home directories for users."
date: 2009-03-18
forum: Server Platforms
---

### Post by dodle on 2009-03-18
ProFTPd creates /home/ftp which is displayed by default when a user logs in, but I want to use a different directory.  Here is the setup for one of my users:```
<Anonymous /home/user/ftp-server/ftp-root>
User user1
Group normal
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /home/user/ftp-server/normal>
<Limit LIST NLST  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>
```

I've been using gProFTPd to configure my settings, but I cannot change the directory viewed at login for this user.

---

### Post by dodle on 2009-03-18
I took the advice of another thread and started with a new proftp.conf file.  Now everythging works.

---

