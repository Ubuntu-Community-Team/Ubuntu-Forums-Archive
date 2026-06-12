---
title: "SFTP limited access to specific user"
date: 2011-11-19
forum: Server Platforms
---

### Post by hillboy2 on 2011-11-19
Running Ubuntu 10.04 as server on a Linode slice. 

I need to give a specific user sftp access to a specific folder. I've followed the directions in this article: [http://library.linode.com/security/sftp-jails]("http://library.linode.com/security/sftp-jails")

When I try to connect with the SFTP remote client the user is authenticated and the SSH session is established but immediately the server closes the connection. The connection for the "root" user works just fine. 

The folder has CHMOD 777. The user is in group filetransfer and his home folder is marked as the appropriate folder in /etc/passwd -> 
jason:x:1000:1000:Jason Hanna,,,:/srv/www/domainname:/bin/bash 

I do not want that user to own the folder but I think the user should have access to the folder and files via "other" permission which is set. However, for now I gave that user ownership of the folder and it still doesn't work.
ls -l ==> drwxrxxrxx 5 jason filetransfer 4096 2011-11-18 20:21 foldername

Any idea why the server is closing the connection? Is there a ssh log file I could look at? 


From SFTP client: 
[12:22:58] Server supported authentications: publickey,password 
[12:22:58] Authentication request. Method: password 
[12:22:58] User authentication successful. 
[12:22:58] SSH session established. 
[12:22:58] Connected to 173.255.---.---. 
[12:22:58] Detected Server Software: OpenSSH 
[12:22:58] Opening channel 0. 
[12:22:58] Server closed connection

---

### Post by volkswagner on 2011-11-26
Have a look at /var/log/auth.log to see if any error show when logging in.

---

