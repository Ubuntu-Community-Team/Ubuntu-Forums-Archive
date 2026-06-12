---
title: "vsftpd FTP Server"
date: 2009-09-02
forum: Server Platforms
---

### Post by danielgroves on 2009-09-02
Hi,  
I have never set-up an FTP server before, and have spent literally hours Googleing around trying to find a solution to this now.  

I have followed the steps in the [documentation]("http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html") to set-up the FTP server, but when I try to connect over the local network I get the following error in FileZilla: 
```
Status:	Connecting to 192.168.1.73:21...
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server
```

Can anyone help me put here?  I would post my /etc/vsftp.conf file here, but I am connecting to my server via SSH and do not know how to copy the content of the file onto my local computer.

Thanks in advance for any help,
Dan.

---

### Post by hessiess on 2009-09-02
Use SFTP instead, much more recent, secure and better designed protocol.

---

### Post by nix4me on 2009-09-02
Your vsftpd needs to be updated to a more recent version.  Filezilla developer decided a few months ago to intentionally break his filezilla client.  His rational was that all ftp servers were wrong.  So he broke filezilla in an attempt to force the ftp server developers to change.  As i stated on the filezilla forumns, it will take months to get all the servers upgraded.

So in short, upgrade your vsftpd to the latest version and it will work fine.

Or, use a different ftp client other than filezilla.

---

### Post by danielgroves on 2009-09-03
> **nix4me said:**
> Your vsftpd needs to be updated to a more recent version.  Filezilla developer decided a few months ago to intentionally break his filezilla client.  His rational was that all ftp servers were wrong.  So he broke filezilla in an attempt to force the ftp server developers to change.  As i stated on the filezilla forumns, it will take months to get all the servers upgraded.

So in short, upgrade your vsftpd to the latest version and it will work fine.

Or, use a different ftp client other than filezilla.

I have just attempted to connect using Cyberduck instead, still no luck.

---

