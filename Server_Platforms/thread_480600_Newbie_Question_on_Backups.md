---
title: "Newbie Question on Backups"
date: 2007-06-21
forum: Server Platforms
---

### Post by stang on 2007-06-21
Hi guys just starting to use Ubuntu and have a question.  I have an Exchange e-mail server that I would like to archive to another server.  Is there any program on Ubuntu that would let me archive e-mail from Exchange 2003 running on Windows 2003 server across my lan to a Ubuntu server?  Thanks!

---

### Post by Mr. C. on 2007-06-21
Is the Exchange server your gateway machine ?

If so, a better, more secure solution would be to put postfix in front of that Exchange server; this will allow you to setup postfix to archive incoming and outgoing messages.  You can also setup additional antivirus / antispam solutions.

MrC

---

