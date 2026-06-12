---
title: "Vsftpd Configuration"
date: 2015-01-15
forum: Server Platforms
---

### Post by cgzapalac on 2015-01-15
I have an Anonymous FTP server setup at /srv/ftp. I'd like to allow "admins" to login and upload files to the server. However, I'm running across two little problems (this is literally the first question I couldn't find an answer to in regular searches online, thus becoming my first post). I think I have allowing the "admins" to log in and only access the files within /srv/ftp (no access to any other part of the system). When ever I try to add the login's for the "admins" the ftp side of the server locks them out. They can ssh just fine. This is really my first venture into FTP so I'm a little lost at the moment. 

Running on Ubuntu Server 14.04

---

### Post by Lars Noodén on 2015-01-15
> **cgzapalac said:**
> I have an Anonymous FTP server setup at /srv/ftp. I'd like to allow "admins" to login and upload files to the server. However, I'm running across two little problems (this is literally the first question I couldn't find an answer to in regular searches online, thus becoming my first post). I think I have allowing the "admins" to log in and only access the files within /srv/ftp (no access to any other part of the system). When ever I try to add the login's for the "admins" the ftp side of the server locks them out. They can ssh just fine. This is really my first venture into FTP so I'm a little lost at the moment. 

If you keep the FTP server, run it as Anonymous FTP server and don't allow password logins.  [FTP is unsafe](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) other than read-only Anonymous FTP.  

The good news is that since you have SSH already working you probably have SFTP already.  SFTP is built into the OpenSSH-server and needs only a little configuration to lock access to a particular directory.  

```

Subsystem sftp internal-sftp

Match Group sftp-admins
        ChrootDirectory /srv/ftp
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

That will lock anyone in the group 'sftp-admins' into using only SFTP and then only inside the directory /srv/ftp.  One detail is that the directory must be owned by root and group root and not writeable by anyone else.  Subdirectories are fine whatever other permissions they might have.

---

### Post by cgzapalac on 2015-01-22
I'll give that a try. Thanks.

---

