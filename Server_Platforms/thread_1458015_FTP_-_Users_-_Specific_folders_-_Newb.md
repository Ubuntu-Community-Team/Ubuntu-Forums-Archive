---
title: "FTP - Users - Specific folders - Newb"
date: 2010-04-19
forum: Server Platforms
---

### Post by tbay007 on 2010-04-19
Okay, so I have been an off and on Ubuntu user.

I am aware this is for Ubuntu 9.10 server edition, but I only installed Ubuntu 9.10.   I like GUI and I think my server is running fine.  I setup SAMBA for local file sharing, but now i am setting up an FTP server.

So I went with this help site:
[https://help.webcontrolcenter.com/KB/a992/vsftpd-ftp-server.aspx](https://help.webcontrolcenter.com/KB/a992/vsftpd-ftp-server.aspx)

I have vsftpd as my program to handle my server.  My issue is this, How do i create another user, with a password, that only allows specific folder access for them.  Like if i wanted to create Anne with password Anne123  and only allow the user to access /home/Annefolder    And not able to move up that directory.  For right now it seems I am able to go whereever I want.

I have been playing around a lot and have finally got frustrated enough to ask for help.

I am still reading up on the forums, but haven't found an exact thing that is a "how to."  I am aware that i am being lazy, i really should read the man addusr and stuff, but I was wondering if this would be a quick answer or not.  If not, tonight I will start reading more info!

Thanks in advance!!!!!

---

### Post by cdenley on 2010-04-19
```

man vsftpd.conf

```
> 
**chroot_local_user**
              If  set  to  YES,  local  users will be (by default) placed in a
              chroot() jail in their home  directory  after  login.   Warning:
              This  option  has security implications, especially if the users
              have upload permission, or shell access. Only enable if you know
              what  you  are doing.  Note that these security implications are
              not vsftpd specific. They apply to all FTP daemons  which  offer
              to put local users in chroot() jails.

              Default: NO


---

