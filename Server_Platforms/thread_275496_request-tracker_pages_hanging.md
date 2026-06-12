---
title: "request-tracker pages hanging"
date: 2006-10-11
forum: Server Platforms
---

### Post by don7777 on 2006-10-11
Hi,

I'm very new to administering an apache server and need some help.

My machine is running Ubuntu6.06 and I installed request-tracker (RT).
As part of the installation for RT, I installed apache2 and users get
to my machine using ssl (https). My machine is connected to the
internet via Verizon dsl.

Local access to the machine via https works perfectly. There are never
any hung pages.

Remote access to the machine very often causes pages to hang (the
progress bar goes about a third of the way at the bottom of my web
browser with some of th page's content showing up).  I cannot figure
out any pattern to this and I'm very confused. I've looked in
/var/logs/apache2/*.log and all appears to be correct.

Where should I start? What should I look at next?

RT uses postgres to store data. How can I determine if its an apache2 problem or a postgres problem? For the moment, I'm assuming its not a postgres problem because local access is working perfectly well.


Thanks for any help,
Don

---

### Post by foxylad on 2006-10-11
I'd first create a page called test.html with the expected HTML, and try accessing that remotely - this should tell you whether Verizon is at fault.

If the test page loads consistently quickly, then you have to start looking at the RT perl script. Log timestamps at various places (sorry, I hate perl so I don't know how to do this off the top of my head) and see what the differences are between local and remote access.

Good luck!

---

