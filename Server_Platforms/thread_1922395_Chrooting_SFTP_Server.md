---
title: "Chrooting SFTP Server"
date: 2012-02-08
forum: Server Platforms
---

### Post by Ambiorix3 on 2012-02-08
Hey Everyone,

I would first like to say that I'm kind of new to Linux. I have some experience but it remains rather limited so I have to rely a lot on tutorials found on the net.

Since a very long time, I would like to set up a FTP Server. Having done quiet a lot of research, I've found that almost nobody recommends using regular FTP, because it sends username and password in clear text. 

So, the alternative is SCP or SFTP. 

I have chosen for SFTP. 

Although I can find numerous articles on setting up an SFTP server under Ubuntu, none of them seem to work for me. 

**_What I would like_**

- A secure FTP server to upload and download files
- Give access to external people (not guests, so they should be password protected)
- Disable Shell access for those people
- Chroot the users to their home directory and give them access to nothing else


**_What I've done_**
Configured openSSH to use internal-sftp as sftp server
Added the following code:

```

Match Group sftponly
ForceCommand internal-sftp
ChrootDirectory /home/%u
X11Forwarding no
AllowTcpForwarding no

```

Added the user to the sftponly group. When I do this, I can't login with winscp with that user, giving me the error: "Network Error: Software caused connection abort.
Using username "xxx".

Authentication failed"

The second I remove him from that group so the "Match Group sftponly" line doesn't match anymore, I'm able to connect with that username.


There is probably a logical explanation for it but I can't seem to find it. Is it even possible what I'm trying to do. 

Thanks in advance

---

### Post by HermanAB on 2012-02-09
Howdy,

SSH with SFTP works out of the box, so all you got to do to make it work, is undo your changes...

---

