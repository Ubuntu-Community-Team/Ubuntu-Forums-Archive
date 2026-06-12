---
title: "Ubuntu FTP Server 10.04"
date: 2010-10-21
forum: Server Platforms
---

### Post by DC1976 on 2010-10-21
I set up an Ubuntu 10.04 FTP Server. 
 
1.) I used fsftpd
2.) I made the following change to the /etc/adduser.conf
 
DHOME = /data
 
DIR_MODE= 0750 (I don't want new users browsing other user's folder or any other folders.)
 
The 0750 doesn't appear to work. When I use FileZilla or connect via command line I'm still able to browse other user folders. (I shouldn't be able too!)

---

