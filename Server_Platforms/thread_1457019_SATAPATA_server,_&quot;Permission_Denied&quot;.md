---
title: "SATA/PATA server, &quot;Permission Denied&quot;"
date: 2010-04-18
forum: Server Platforms
---

### Post by mfcallahan on 2010-04-18
I'm currently running Karmic on a old Dell Pentium 4, and I am having trouble copying files to this box from my laptop which is running Linux Mint Helena.  I am able to see and connect to the shared directory on the Dell, copy and execute files from there, but cannot write to it.  The permissions have been set to 777 on the shared directory and sub directories within that.  The older Dell has a PATA hard disk, 300gb, while my newer laptop has a SATA hard disk.  I've read that this can be a problem, and permissions may not be recognized?  I'm not able to connect to the laptop from the Dell, neither of the administrator logins  work, though I maybe need to do this as root?  Here is the smb.conf file I am running on both machines:

[global]
workgroup = MSHOME
[homes]
guest ok = yes
read only = no
[share]
path = /home/matt/Shared
comment = Shared files

Long story short, I want to be able to write to my server, not just read and execute.  I am also not able to write to the server when logged on to a windows machine on the same network.  Any thoughts would be appriciated if you've experienced a similar situation.

Thanks,
Matt

---

### Post by mfcallahan on 2010-04-18
disregard this, I installed webmin, and all is a-ok.

---

### Post by SRST Technologies on 2010-04-18
If you find the answer to your own problem, it's a good idea to post what you did that fixed it.  There's more than just you on the net using this OS.  Others can benefit from your knowledge.

I am almost sure that he forgot to put "read only = no" on his share declaration.  "read only = no" without the quotes on a single line tells samba to allow people to write to that share.

---

