---
title: "Spamassassin Segfault"
date: 2008-11-25
forum: Server Platforms
---

### Post by sdnelson on 2008-11-25
Just checking to see if anyone has had this problem. 

I am running Ubuntu 8.04.01 Server with Postfix, Procmail, and Spamassassin. Individuals emailing back and forth to one another or to outside folks works great, however, when emailing to a group list in the aliases file, ie. testgroup: :include: /home/snelson/mygroup.txt causes a "spamassassin segfault" with either an error 4 or 5 or 14. 

So, to make a long story longer, I decided to debug the spamd portion using the -D option and to my surprise - no more segfaults.. Now I am totally baffled. 

Has anyone seem this before? Just want to make sure I haven't lost all of my marble. :KS

---

