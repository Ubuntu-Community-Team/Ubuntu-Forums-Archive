---
title: "Strangest Problem Ever seen"
date: 2010-10-13
forum: Server Platforms
---

### Post by pktrivedi on 2010-10-13
Hello, I have a problem with NFS which the strangest I have ever seen.

We have an NIS+NFS server running on "Ubuntu Hardy 8.04 LTS"
Clients are Fedora, Ubunut 9.10, 10.04, Mint ...etc. Ubunut clients have edubuntu artwork only. There are not more than 10 clients which regularly connect to the server.

After 1 month of fine performance suddenly one day users complained about not being able to logon. That the screen hangs with only mouse cursor without desktop loading. This happened to all clients and all users, except one running Fedora-13 which became very slow but users are able logon to that machine and access their files.

Upon investigation I found that instead of logging on to the GDM, if one goes to the terminal using CTRL+ALT+F*, everything works perfectly fine. User are able to access the files, modify them save them. 
Server syslog also has entries saying authenticated mount request from clients.

What could have gone wrong after one month?

---

### Post by s_raghu20 on 2010-10-13
> **pktrivedi said:**
> 

What could have gone wrong after one month?

Perhaps some update ?? do you have automatic update installation enabled ??

---

### Post by pktrivedi on 2010-10-13
Nope, Automatic Updates not enabled but after this problem I updated and upgraded server as well as clients except fedora-13.

---

### Post by SeijiSensei on 2010-10-13
Are you using the same NFS version throughout?  Perhaps the upgraded NFS server uses NFS4 while the clients are expecting NFS3?  You can force the version on both the server and client side.  See the man pages for details.

---

### Post by pktrivedi on 2010-10-13
> **SeijiSensei said:**
> Are you using the same NFS version throughout?  Perhaps the upgraded NFS server uses NFS4 while the clients are expecting NFS3?  You can force the version on both the server and client side.  See the man pages for details.

We upgraded after the problem started. The same configuration was working for 1 month and suddenly this weird thing started.
And both client and server use same NFS3 version.

---

