---
title: "Email Server Problem Ubuntu"
date: 2008-12-23
forum: Server Platforms
---

### Post by jasonralston on 2008-12-23
I used the two below articles to set up my email server which works great other then the fact I can't get outlook or SquirrelMail to see the mailbox but webmin /"postfix read email" see's it? How do I get the default set to my maildir file? 

I'm using the following procmail recipe to deliver my mail. 


The Perfect Server - Ubuntu Intrepid Ibex (Ubuntu 8.10)
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)



DROPPRIVS=yes
:0fw
| /usr/bin/spamc
:0
* ^X-Spam-Status: Yes
$HOME/maildir.spam
:0
* ^X-Spam-Status: No
$HOME/maildir

---

