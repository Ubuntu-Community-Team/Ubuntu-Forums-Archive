---
title: "Ubuntu 14.04 LTS SSH Issue"
date: 2015-12-24
forum: Server Platforms
---

### Post by paul212 on 2015-12-24
I am running a Ubuntu 14.04 LTS server.  I have set it up to do SFTP.  Works Great. Now here is the problem.  I did all the recommended fixes for Logjam.  I am able to SSH into the server using Putty.  I can do SFTP transfer using FileZilla.  But I cannot SFTP into the server using WS_FTP.  I get 
[SIZE=1][COLOR=#ff0000][SIZE=1][COLOR=#ff0000][SIZE=2]Failed SSH Key Exchange

[/SIZE][COLOR=#000000][/COLOR][COLOR=#000000][SIZE=2]Has anyone run into this issue? Is there a fix for WS_FTP?   I have many different users who use this SFTP server daily and some use WS_FTP. 

Any help would be great!  Thank you[/SIZE][/COLOR]



[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by TheFu on 2015-12-24
If WS_FTP is a commercial product, contact their support team.  Do they have any log files that can provide more detailed connection information?  On the server-side, you an turn up the log levels by running openssh-server with more verbosity. [https://en.wikibooks.org/wiki/OpenSSH/Logging](https://en.wikibooks.org/wiki/OpenSSH/Logging)

Also, make certain the users are using sftp, not the ftps protocol. 

As an alternative, I can recommend winscp for the drag-n-drop needy.

---

