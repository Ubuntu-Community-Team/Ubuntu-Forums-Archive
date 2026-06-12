---
title: "filezilla client open too many connections"
date: 2007-04-30
forum: Server Platforms
---

### Post by mojoman on 2007-04-30
Hi all,

I'm running a small ftp-server using glFTPd and I got it set up so that a user is limited to two simultaneous logins. It's connected to my router, as is a couple of other computers.

When I connect to it from my desktop using gFTP it opens two connections at the same time. All is good (exept that I really don't like gftp).  When I connect to the server using filezilla it tries to open one connection for each file that I want to download or upload. This is not good at all.

Now, when I connect to another ftp-server, this one external, with filezilla it opens two connections and  leave it at that, just like gFTP does on my server.  I've compared the settings in site manager for my server and the external server and they are identical. I've also tried to set the limit to the number on connections allowed to two, as this is what the server allows (which seemed like the logical thing to do). No good. 

I'm at my wits end here. Why does filezilla persist in opening so many connections when I'm connected to this server and not to other?

The filezilla I'm using is from the repo's, runing on xubuntu feisty. glFTPd is compiled from source, but as gFTP does not behave like filezilla I suppose the problem is with filezilla. Does anyone have a take on why filezilla acts like it does?

Thanks
/mojoman

---

### Post by lhtown on 2007-04-30
Could it be an issue of an active or passive ftp connection?

---

### Post by mojoman on 2007-05-01
> **lhtown said:**
> Could it be an issue of an active or passive ftp connection?

No, that was one of my takes as well but the only thing that changes is that with a passive connection, the speed is about 25% of an active. Still tries to open one connection for each file.

---

### Post by mojoman on 2007-05-06
Could I just *bump* this one?

Thanks for any and all help.
/mojoman

---

