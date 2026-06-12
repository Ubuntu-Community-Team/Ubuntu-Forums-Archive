---
title: "can ubuntu server do this?"
date: 2007-12-14
forum: Server Platforms
---

### Post by terrifiedkiller on 2007-12-14
hiyas

less then a week ago i decided to go try setting up my own client/server (domain model) network and downloaded teh 120 trial version of windows server 2003 had everything working perfectly a week later however its telling me my evaluation period is over i double checked and found out it was in fact 120 day trial i had active directory and file server runnign just fine but i had a few issues 1 being i had to have 6 network drives (i have 3 hard drives on server 1 80 gig and 2 160 gigs and was giving family access to one that only they could access and 1 everyone can access) would ubuntu server easily let me setup a domain like active directory that windows linux and macs can connect to and would there be a way to make it so one network drive gets access to all 3 hard drives? also i would like to be able to remotely administer the server any advice would be appreciated

---

### Post by mellowd on 2007-12-14
You can use Samba as a domain controller but Samba 3 still uses NT4 type domains. 

You can also administer your server through ssh from anywhere (it's what I do)

---

### Post by terrifiedkiller on 2007-12-14
> **mellowd said:**
> You can use Samba as a domain controller but Samba 3 still uses NT4 type domains. 

You can also administer your server through ssh from anywhere (it's what I do)
would there be any usefull tools to configure samba as i found manually configuring the config file confusing and would this work on xp pro ?

---

### Post by terrifiedkiller on 2007-12-14
also could i use a 64 bit server and have 32 bit clients with this?

---

### Post by mellowd on 2007-12-14
> **terrifiedkiller said:**
> would there be any usefull tools to configure samba as i found manually configuring the config file confusing and would this work on xp pro ?

There is. Here are a number of GUI tools I've found on the samba page - [http://us1.samba.org/samba/GUI/](http://us1.samba.org/samba/GUI/)

It also comes with a web configurator now but I've always done my config through text files so I can't remember the exact name of it now

---

### Post by daengbo on 2007-12-14
I'm a died-in-the-wool Ubuntu user, but I'm going to suggest something outside Ubuntu for you. Look at eBox Server ( [http://ebox-platform.com](http://ebox-platform.com) ). You will find the interface easy and everything is set up for you.

Cheers.

---

### Post by tgalati4 on 2007-12-14
Lacie makes an external 500 GB drive that has a file and printer server built in.  It runs an imbedded Linux.  At $200 it's competitive with Windows Server and you get a disk drive.

---

### Post by terrifiedkiller on 2007-12-14
another thing the computer i'm using as a server has a 645 bit proccessor would it be possible to have the server use 64 bit os and software and have the clients (my 3 computers at home) be running 32 bit xp pro and connect to the domain?

---

### Post by mellowd on 2007-12-14
> **terrifiedkiller said:**
> another thing the computer i'm using as a server has a 645 bit proccessor would it be possible to have the server use 64 bit os and software and have the clients (my 3 computers at home) be running 32 bit xp pro and connect to the domain?

64bit I assume? Yes you can do that.

My server has a 64bit but I'm more than happy with the 32bit version of ubuntu server

---

### Post by terrifiedkiller on 2007-12-14
> **mellowd said:**
> 64bit I assume? Yes you can do that.

My server has a 64bit but I'm more than happy with the 32bit version of ubuntu server

so the 64 bit wont improve the performance? also one issue i had with 2003 was at first nobody could install anything while logged in how do i enable that with samba?

---

### Post by mellowd on 2007-12-14
> **terrifiedkiller said:**
> so the 64 bit wont improve the performance? also one issue i had with 2003 was at first nobody could install anything while logged in how do i enable that with samba?

I don't completely understand what you mean by the second question

---

### Post by terrifiedkiller on 2007-12-14
> **mellowd said:**
> I don't completely understand what you mean by the second question

when i first got my windows server 2003 network going all users couldnt install any programs which turned out to be a user rights issue i had to promote the 3 users to the domain admin group in order for anyone to be able to install anything apparently the administer group wouldnt do would samba take care of this issue?

---

### Post by mellowd on 2007-12-14
> **terrifiedkiller said:**
> when i first got my windows server 2003 network going all users couldnt install any programs which turned out to be a user rights issue i had to promote the 3 users to the domain admin group in order for anyone to be able to install anything apparently the administer group wouldnt do would samba take care of this issue?

I haven't as yet used samba as a domain controller, but I would assume that the user would need admin rights to install applications on any PC. They could be granted administrators for their respective PC's only. They wouldn't need to be domain administrators.

---

