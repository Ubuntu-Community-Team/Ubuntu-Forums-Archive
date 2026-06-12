---
title: "Active Directory"
date: 2012-09-19
forum: Security
---

### Post by pmon on 2012-09-19
I'm trying to use Likewise to add my machine to an Active Directory.  I don't have an administrator account that will allow me to join the AD.  I'm wondering if there is a workaround in my case because I have been informed that the PC has been 'manually' added to the domain already.  I was given a host name to use at installation time.

Apologies if my understanding of how this works is wrong.  I've never been involved in Windows networking at this level before...

---

### Post by Ms. Daisy on 2012-09-20
If you don't get an answer here you may try the powerbroker forum

[http://forum.beyondtrust.com/](http://forum.beyondtrust.com/)

---

### Post by pmon on 2012-09-21
Good call, thanks!  I'm going to tackle this further on Monday, will post on the suggested forums if I'm still stuck & if no-one here has any info by then.

---

### Post by pmon on 2012-09-24
The eventual resolution to this issue was that someone with a suitable network administrator user ID and password came along and entered the required details.  So, not too sure if it is possible to add a machine to the network manually/remotely and then authenticate without having to have the AD administrator actually get involved locally.

---

### Post by thnewguy on 2012-09-24
To join a Active Directory domain you do need a network admin's credentials. I think the admin could technically login remotely to do that, but they would have to have a local admin account on your machine and remote access set up on your machine. Really, it's a pain, regardless of which OS is the client.

---

