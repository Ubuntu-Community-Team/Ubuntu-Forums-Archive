---
title: "webmin/syscp/other  Whats the best Lucid 32 bit dev environment"
date: 2011-10-10
forum: Server Platforms
---

### Post by jazzon on 2011-10-10
I am trying to learn the ins and outs of admining a server suite.  Database/Mail (Dovecot-Postfix), LDAP, WWW/FTPS on seperate machines on a local lan.  This is a practice and learning environment for me.

Which admin suite would be the most useful?  Translate useful to equal user friendly, ease of use and installation, up to date, and most powerful (will sacrifice ease of use for muscle)  Easier to foul things up and therefore learn to fix with a powerhouse app.  (No I do Not Claim To Be Sane.)

---

### Post by jazzon on 2011-10-11
still need some input here folks

---

### Post by reddevil2064 on 2011-10-11
> **jazzon said:**
> I am trying to learn the ins and outs of admining a server suite.  Database/Mail (Dovecot-Postfix), LDAP, WWW/FTPS on seperate machines on a local lan.  This is a practice and learning environment for me.

Which admin suite would be the most useful?  Translate useful to equal user friendly, ease of use and installation, up to date, and most powerful (will sacrifice ease of use for muscle)  Easier to foul things up and therefore learn to fix with a powerhouse app.  (No I do Not Claim To Be Sane.)

Shell of your choice. BASH, csh, tsch...list goes on. If you want power there you go. Log in as root and have at it. Admin suites hold your hand, and if you're wanting to learn you shouldn't even be looking at them. I suggest buying a book or two and brushing up on some basics and then diving in, one service at a time. Apache is pretty easy to get going, so are most FTP configs.

This is a pretty great resource as well : [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by jazzon on 2011-10-11
lol

very true.

2 problems though.

One is I am permenantly unemployed due to disability and computer related books cost more than I can afford;

and two is that apache , ftp, mysql I know.  The rest I am totaly  totally TOTALLY not understanding as i research the stuff.

Mailservers are cunfusing the hell out of me.  My goal is to use the web-interface type things to make changes, (from one thing that works to another) and then pick apart the conf files to see how it was done.

But if the interfaces arent good they can make bad changes, and I wouldnt know a good one from a bad one as I use ssh most of the time.

---

### Post by reddevil2064 on 2011-10-11
Well, google is still free, that guide will hold your hand part of the way through set up. After you get things up and running through command line I would suggest something else then. Server admin is easier,faster,safer,more-fun, etc through command line.

If you are absolutely going to install a web interface though, I would suggest webmin. It's pretty well supported.

---

