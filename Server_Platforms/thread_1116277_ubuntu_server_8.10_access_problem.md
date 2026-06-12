---
title: "ubuntu server 8.10 access problem"
date: 2009-04-04
forum: Server Platforms
---

### Post by peithos on 2009-04-04
Hi,
I have some experience with Ubuntu desktop but today is my first foray into anything got to do with 'servers'.
I have clean installed Ubuntu 8.10 Server on an old Gateway tower - 450MHz CPU, 384 RAM and 15GB hard drive. I set it as a file server only - nothing fancy.From another XP Home PC I can see this server in windows networks/Workgroup, it's called 'ubuntuserver' and a sub-folder in it called 'printers and faxes'.
So I presume I'm half way there. I have installed samba and nfs. I have read loads about editing /etc/exports to try and get it to share my /home folder.But try as I might I can't get it to work. This is where my CLI abilities let me down - I'm poor on syntax and hostnames etc... What do I have to do to get the XP box to see the /home on the server and also how do I create a folder on the server and populate it with files to share? The Ubuntu documentation instructions presume too much base knowledge! Any help appreciated.

---

### Post by cariboo on 2009-04-04
Windows  does not work natively with NFS. I would suggest using Samba. Have a look at this [thread=202605]howto[/thread].

Jim

---

