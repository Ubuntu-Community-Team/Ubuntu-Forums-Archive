---
title: "firestarter help!!!!"
date: 2007-08-15
forum: Server Platforms
---

### Post by proctor-michael on 2007-08-15
I have just done a clean install with ubuntu 7.04.  When I added firestarter, It didn't come up on the menu, like it had with 6.06 lts.  I removed it and tried to reinstall it again; same thing.  I was wondering what I am doing wrong!  Also do I really need a firewall with this operating system?  It is so much more secure than windows.  I will listen to all views.  Thanks in advance,
Michael

---

### Post by wieman01 on 2007-08-15
First off, you don't really need a firewall provided that you have no services running that are not supposed to accept connections with other PCs, etc. Rather than configuring the Linxu built-in firewall via Firestarter, you could simply turn off all service (e.g. ssh, ftp) which you do not need. 

Second, you can always start up Firestarter by means of command line:
> sudo firestarter
Then enter your password and there you are.

I use Firestarter nonetheless because I want to have full control of the system. That allows me to block all services that I use in my home network when I am on the road and have to use others' networks. 

Post here if you have further questions.

---

