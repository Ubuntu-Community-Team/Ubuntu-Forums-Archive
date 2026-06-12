---
title: "Ubuntu Server: FTP Server Options?"
date: 2009-02-20
forum: Server Platforms
---

### Post by Phillyman on 2009-02-20
I am thinking of moving to Ubuntu for my home server, its basically just a slimline HP computer that runs a file server and ftp server. The only issue holding me back is the FTP server software I have. I am running Gene6 FTP Server with a few plug-ins.

Its basically the plug-ins that have me tied to Gene6 and thus Windows. 

The Plug-in does the following....

If (X) number of incorrect password attempts on a login....lock the account.

If (X) number of incorrect passwords total, ban the IP.

So lets say a user tries to log in with the username "bob", after his 3rd incorrect password....the account "bob" is locked, if that same IP now tries to log into account "sara" it will keep a running total of incorrect tries....and eventually ban that IP from even connecting to the FTP server.

If I could get a similar functionality in a linux based FTP server....I could switch in a heart beat!

Oh and all the normal goodies also....

Limit bandwidth per day/week
Limit access times per usergroup/username
Limit bandwidth speeds (uploads/downloads)
Auto Ban for hammering the FTP
etc..

Thanks for your time

-Phillyman

---

### Post by HermanAB on 2009-02-20
Of course, all of that can be done, but there is no single application for it, since it involves multiple subsystems.

However, since FTP is inherently insecure, there is not much point in layering on features to try and protect it.  It would be better to simply use SSH and SFTP, which is inherently secure and then doesn't need all the layers of crud on top.

Cheers,

Herman

---

### Post by 3L33T on 2009-02-20
> **Phillyman said:**
> 
The only issue holding me back is the FTP server software I have. I am running Gene6 FTP Server with a few plug-ins.


Try Gene6 on Wine.   

As for ftp sever, I've used vsftpd in the past on a personal DELL SC420 internet-facing server and had no security issues with it in Fedora/redhat enterprise linux and ubuntu flavor.

---

### Post by spiderbatdad on 2009-02-20
Also recommending sftp via openssh. fail2ban is quite easy to configure for banning ipaddress issueing bad login attempts. Additionally ssh is easy to configure to allow only specified usernames and groups.

---

