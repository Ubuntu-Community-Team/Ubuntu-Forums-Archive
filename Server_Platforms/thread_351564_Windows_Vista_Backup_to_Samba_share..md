---
title: "Windows Vista Backup to Samba share."
date: 2007-02-02
forum: Server Platforms
---

### Post by gunck8 on 2007-02-02
There seems to be a problem with the Samba server that comes as standard package (version 3.0.22) with Ubuntu. When I start Windows Vista Backup on my workstation and define my Xubuntu (Edgy) server's Samba share as destination I get the following error message on my Vista:

"The network share could not be accessed for the following reason:
Cannot create a file when that file already exists. (0x800700B7)
Please ensure that the network location is valid."

I have googled around and it seems like many others have the same problem. I found an intresting link where a guy has explained what probably seems to be the problem:

[http://www.nabble.com/ACL-issue-w-Vista-backup-t3145296.html#a8719080]("http://www.nabble.com/ACL-issue-w-Vista-backup-t3145296.html#a8719080")

-gunck8

---

### Post by tomBorgia on 2007-02-02
> There seems to be a problem with the Samba server

It could be a new, undocumented "feature" in Vista, Samba has worked for years with winXP / win2K... 

Am I being cynical? Pehaps...

---

### Post by victor_c26 on 2007-02-19
As I stated in another thread:

Apperantly Microsoft created a new standard called SMB2. So until Samba get's updated with the new standard, we're going to have to use XP to transfer files over to our Linux boxes.

---

### Post by dbutcher on 2008-01-05
I was going to start a new thread, but this one is right on point for my question.
I'm running Dapper 6.06 with Samba 3.0.22. 

I had also seen the other posting that gunck8 refers to, but I don't know how to incorporate this into a solution.
I also see here [http://www.samba.org/samba/patches/](http://www.samba.org/samba/patches/) that there is an official patch under Bug 4361, but again, I don't know how to make this work.

I'd appreciate any thoughts on how to implement these fixes.
Cheers,
Dave

---

