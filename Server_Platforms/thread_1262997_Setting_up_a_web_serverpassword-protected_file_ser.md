---
title: "Setting up a web server/password-protected file server"
date: 2009-09-10
forum: Server Platforms
---

### Post by askantik on 2009-09-10
Hi,

I know diddly squat about Linux, so I have to ask some basic questions.  I'm looking to build a computer to host a basic website (probably pretty low traffic) and also have an area where I can have password-protected file transfer.  It's in a university lab, so I think bandwidth should be decent.

Questions:

1) I read this guide ([http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)) and it seems straight-forward enough.  Will that allow me to both host my website and have password-protected file storage (users from outside the university will need to be able to verify their credentials and both upload and download files)?

2) If the answer to number 1 is yes, how much of a machine do I need?  I want it to be adequate without going overboard, but unfortunately I haven't the slightest idea of what's necessary.  For example, is a basic dual-core Athlon with 2GB of RAM enough?  I'll be running 2 SATA 1TB drives in Raid 1 configuration if I can figure out how to set that up (never set up RAID before).

And finally, any additional tips or advice is greatly appreciated.  This is a new area for me-- I'm comfortable building computers, but I know little about Linux and even less about RAID or setting up servers.  Thanks :)

---

### Post by recentcoin on 2009-09-10
1) I'd recommend forcing users to use SSH or SSL to authenticate and to encrypt the uploads and downloads.  FTP uses clear text for both.  

2) If you're at a University, there should be an IT person there who can guide you through the proper steps or let you know if something like that already exists.  Odds are, it already does.  

3) Your machine should be fine.  But you will need to either configure LDAP and local accounts or just local accounts, which you will need to manage.  

4) Look at Liferay - [www.liferay.com](www.liferay.com).  There's some very good file and document management built into the portal.  

5) Unless people are going to be loading a lot of files at one time, I'd suggest using Webmin or some sort of portal software to manage it.

---

### Post by Sporkman on 2009-09-10
> **askantik said:**
> 2) If the answer to number 1 is yes, how much of a machine do I need?  I want it to be adequate without going overboard, but unfortunately I haven't the slightest idea of what's necessary.  For example, is a basic dual-core Athlon with 2GB of RAM enough?  I'll be running 2 SATA 1TB drives in Raid 1 configuration if I can figure out how to set that up (never set up RAID before).


More than enough.

My website went through a busy spurt a couple of years ago, where I was getting 10K+ hits/day, and running computationally heavy image processing apps. The machine was a dedicated server with an Athlon 2000k (competitor to a P4) & 256mb RAM. The thing hardly broke a sweat.

Really, it's just desktop apps that chew up CPU cycles & memory. Server applications require very little resources in comparison. The biggest limiting factor tends to be bandwidth.

---

### Post by askantik on 2009-09-10
Thanks, Sporkman.  You think a lowly machine such as the one you described would also be OK for a file server?  As recentcoin said, I may be able to get help from the IT dept on that one, but just in case.  I'm not exactly sure how big the files will be (I don't actually work in the lab, I'm helping someone) but I can't imagine that they'd be all that big or that the transfer would be all that numerous.

---

### Post by Sporkman on 2009-09-10
> **askantik said:**
> Thanks, Sporkman.  You think a lowly machine such as the one you described would also be OK for a file server?

Absolutely - as long as the harddrive isn't too old & crappy of course. :) CPU & RAM resource-wise, however, you need very little.

---

