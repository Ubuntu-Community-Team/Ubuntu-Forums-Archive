---
title: "can't login via sftp"
date: 2016-05-01
forum: Server Platforms
---

### Post by Drone4four on 2016-05-01
I haven't changed any settings on my remotehost.  What's different now is that last week I reformatted my 14.04 localhost to 16.04. I was able to preserve my home folder perfectly, so my rsa keys for logging via ssh in to my remotehost works perfectly.  But I can't figure out my my sftp client (konqueror) won't let me login.  I ensured sftpcloudfs is installed on both the remotehost and localhost.  Here is the notification I see upon attempting to login via sftp:
```
The requested operation could not be completed

Details of the Request:

URL: sftp://user@remotehost/var/www/
Protocol: sftp
Date and Time: Sunday, May 01, 2016 10:53 PM
Additional Information: The host key for this server was not found, but another type of key exists. An attacker might change the default server key to confuse your client into thinking the key does not exist. Please contact your system administrator.
Description: The host key for this server was not found, but another type of key exists. An attacker might change the default server key to confuse your client into thinking the key does not exist. Please contact your system administrator.

```

Since I haven't changed anything on my remotehost, the two users are still marked down as in the ssh/sftp user group.
Filezilla out puts this:
```

Status:	Resolving address of remotehost
Status:	Connecting to 192.xxx.xxx.xxx
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server
```

I feel like the answer to my question is gonna be real trivial - - something that I should already know.

Thanks for your attention.

---

### Post by volkswagner on 2016-05-02
On the client look at ~/.ssh/know_hosts for entries with the ip or hostname.
Is it possible you connect with ssh using a different ip or hostname or alias?

Try deleting any entries related to the remote server.

---

### Post by Drone4four on 2016-05-02
First I backed up my known_hosts, then removed the original file.  This enabled me to log in via ssh and sftp perfectly.  I don't really understand why this worked. I found a really great, [detailed stackoverflow explanation of the known_hosts file]("http://security.stackexchange.com/questions/20706/what-is-the-difference-between-authorized-key-and-known-host-file-for-ssh"), but I don't really understand it.  Ah well.  Thanks **volkswagner** for your help.

---

