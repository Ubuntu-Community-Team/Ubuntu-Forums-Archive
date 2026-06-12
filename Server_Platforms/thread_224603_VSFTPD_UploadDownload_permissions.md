---
title: "VSFTPD Upload/Download permissions"
date: 2006-07-28
forum: Server Platforms
---

### Post by goldwinger on 2006-07-28
I have VSFTPD setup and my users can login from the web and upload files. But when they try to download a file from a different user they can not because the file is set to (Owner RW.) Can anyone suggest a setup that will allow uploads to be accessible for download by anyone who has login rights. 


Thanks
Joe

---

### Post by Sureshot324 on 2006-09-24
I have the same problem.  My FTP server is set for anonymous login.  People can upload files to it, but the permissions are set to -rw-------.  This means that only the owner can access them.  People who anonymously login to my ftp server can't even download them.  I have to manually change the permissions of each file so that anonymous users can download them.

I want all uploaded files to have read permissions for all users so that anyone can download files that were uploaded by anonymous users.

I've tried editing /etc/vsftpd.conf and changing anon_umask to different things like 000, 777, and 022 but nothing worked.

---

### Post by K.Mandla on 2006-10-01
There's a local_umask variable that, if I understand it right, sets file permissions to uploaded files.

[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

It seems that default is 077. Perhaps that will help?

---

### Post by mslonik on 2006-11-29
I have the same problem. After several hours of googling around I see that many people have the same problem, but till now nobody have provided a solution. Please halp!

Regards,
Maciej (mslonik)

---

### Post by stell86 on 2006-12-10
from here:[http://www.vsftpdrocks.org/faq/]("http://www.vsftpdrocks.org/faq/")
> Here is a copy of the official vsftpd FAQ that is included in the vsftpd package

> Q) Help! Uploaded files are appearing with permissions -rw-------.
A1) Depending on if this is an upload by a local user or an anonymous user,
use "local_umask" or "anon_umask" to change this. For example, use
"anon_umask=022" to give anonymously uploaded files permissions
-rw-r--r--. Note that the "0" before the "22" is important.
A2) Also see the vsftpd.conf.5 man page for the new "file_open_mode"
parameter.

and then from here:[http://vsftpd.beasts.org/vsftpd_conf.html]("http://vsftpd.beasts.org/vsftpd_conf.html")
> file_open_mode
    The permissions with which uploaded files are created. Umasks are applied on top of this value. You may wish to change to 0777 if you want uploaded files to be executable.

    Default: 0666 

---

### Post by mslonik on 2006-12-11
Yes, I know. I can read. Nevertheless even with properly set anon_umask option it doesn't work. Please have a look to my bug report on that subject:

[https://bugs.launchpad.net/distros/ubuntu/+source/vsftpd/+bug/74173](https://bugs.launchpad.net/distros/ubuntu/+source/vsftpd/+bug/74173)

Please help to confirm it!

Kind regards,
Maciej (mslonik)

---

### Post by cutter00 on 2006-12-14
> **goldwinger said:**
> Can anyone suggest a setup that will allow uploads to be accessible for download by anyone who has login rights. 


> man vsftpd.conf
...
 **anon_world_readable_only**
              When  enabled, anonymous users will only be allowed to download files which are world readable. This is recognising that the ftp user may own
              files, especially in the presence of uploads.

              Default: **YES**
...

Try set that option to ``NO''.

---

### Post by mslonik on 2006-12-14
cutter00: No, it doesn't work either with anon_world_readable_only. Please help and confirm this bug!
[https://bugs.launchpad.net/distros/ubuntu/+source/vsftpd/+bug/74173]("https://bugs.launchpad.net/distros/ubuntu/+source/vsftpd/+bug/74173")

Thanks,
mslonik (Maciej)

---

### Post by stell86 on 2006-12-15
> **mslonik said:**
> Yes, I know. I can read. 
Apologies for unintended offence.  I was going through similar issues with VSFTPD and also could not find how to limit 'anonymous' to read-only and without 'dir-list'.
I've switched to ProFtp in the meantime.

> 
Nevertheless even with properly set anon_umask option it doesn't work. Please have a look to my bug report on that subject:
[https://bugs.launchpad.net/distros/ubuntu/+source/vsftpd/+bug/74173](https://bugs.launchpad.net/distros/ubuntu/+source/vsftpd/+bug/74173)
Please help to confirm it!

I've seen the buglist-site the first time following your link.  What do you need from me to support/confirm this problem?  Would a simple ' Yes - me too' be enough or is more needed?  Again, I'm new to this error/bug-reporting: Is reporting it to 'ubuntu' enough or do we need to report it to the VSFTP-developers? Is this only limited to ubuntu? I was trying to use it on Ubuntu server (upgraded from 5.10 to 6.06 to run on older hardware).

Retief

---

### Post by cutter00 on 2006-12-15
What purpose do you follow?
You have a list of registered users which can write to ftp and anonymous users which could not write but could read. vsftpd writes files, which have permissions -rw------ and are owned by ftp:nogroup (this pointed in vsftpd.conf).
Do i understand rightly?

---

### Post by stell86 on 2006-12-15
> **cutter00 said:**
> What purpose do you follow?

I'm going to presume this relates to me - and if not - please indicate - I don't want to hijack someone else's thread:
I wanted to limit 'anonymous' to read-only (which I understood)), but even limit further by not allowing directory listing - ie. if anonymous wants to download, he/she needs the correct filename and location beforehand.  Files are uploaded via an user account with a datetimestamp. This is how the application works that's used with the Ftp-server.  I couldn't find how to deny dirlisting in VSFTPD - in ProFtp it is a combination of [WRITE LIST] DenyAll (roughly abbreviated).

---

### Post by mslonik on 2006-12-17
> **stell86 said:**
> Apologies for unintended offence.  


I don't mind. Sometimes on forums answers look more roughly then it is intended.


> **stell86 said:**
> 
I've seen the buglist-site the first time following your link.  What do you need from me to support/confirm this problem?  


At least please leave a message that you face the same problem. It will suggest to people who take care about this bug to pay some more attention to it. You probably are not allowed to confirm it.

Thanks for your attention,
mslonik (Maciej)

---

### Post by mslonik on 2006-12-17
cutter00: I follow the following purpose: If someone (anonymous user) wants to upload e.g. photos after weekend and share those photos with friends, than he (she) is allowed to copy them to server, but that is all. He (she) is not allowed co copy them from server to his (her) machine, and nobody of anonymous users does in fact.

I don't want to have a list of registered users but to drive anonymous server.

Please help to support this bug. Write a short comment that you have the same problem here:
[http://https://bugs.launchpad.net/distros/u...tpd/+bug/74173]("https://bugs.launchpad.net/distros/u...tpd/+bug/74173")

---

### Post by LongMan[RUS] on 2007-10-06
i solved this problem for my inet-isolated network:
```

local_umask=000
anon_umask=000

```
If i add file_open_mode=777, uploaded files get -rw------- permissions, so i preferred to yse default, that works.
000 for umasks is not too secure,  but it works )

---

### Post by loadeddreams on 2007-11-06
This resolution does not work and the bug link does not work either... was this ever resolved?

---

### Post by AvWijk on 2008-01-23
same problem here. Files stayed locked, only CHMOD 700 rights.
Is this bug still unsolved?

---

