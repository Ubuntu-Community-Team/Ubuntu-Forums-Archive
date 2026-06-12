---
title: "Fileserver in office enviroment"
date: 2007-06-09
forum: Server Platforms
---

### Post by TradiZ on 2007-06-09
Hi all,

I need some help with directions since I fail to search my way to the solution,

I have a fresh 7.04 server install and I want to use it as a file server where clients are mainly windows XP but also Ubuntu 6.06, 6.10 & 7.04.

15 users created in 3 different groups, works excellent locally. Samba installed. Firehol as firewall.

Now, I need some kind of login scripts, since client users login from various computers I need a login-script that connects the login windows user to the right shares on the 7.04 server.

This Login script will be for 15 win XP clients and 3 Ubuntu clients.

The shares are as follows: 

Users home, (normal home folder, only user allowed)
Department application (which users group have full access to)
Corp admin (which 1 of each department have access to.)

So if User A logs in on WinXP client A, he gets his folders, and if he logs in from WinXP client B, he should also get his folders as well as if he is login in from a Ubuntu box.

I guess what I want is the functionality same as for a win domain server. But instead using Ubuntu server,


Anyone have a solution or guidance to where I find howtos... :-)

Thanks,

TradiZ

---

### Post by obimeister on 2007-06-09
Then you want samba act like a PDC in windows environment. From gentoo wiki I found pretty good documentation:[http://gentoo-wiki.com/HOWTO_Implement_Samba_as_your_PDC]("http://gentoo-wiki.com/HOWTO_Implement_Samba_as_your_PDC")
There are some gentoo specific stuff but configuring samba should be same. Or you can try use swat to configure samba also.

---

