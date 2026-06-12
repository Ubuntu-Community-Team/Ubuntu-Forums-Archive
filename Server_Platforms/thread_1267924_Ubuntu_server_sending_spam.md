---
title: "Ubuntu server sending spam"
date: 2009-09-16
forum: Server Platforms
---

### Post by jopoli697 on 2009-09-16
Hi, my name is Jorge and i have a problem with my ubuntu server that has running postfix+dovecot and squirrelmail for my email server, however, i have noticed that to some accounts that i have created ( i have like 20 accounts created) the squirrelmail interface is diferente color, normal color is gray and white and to other accounts ( like 2 ) the colors are brown, white and green, and also when i check these accounts sent mail, i see like 2000 sent mails but with other email adress so i checked in some forums and i thought this could be an "open relay" problem, but i checked some "open relay" tests in the web and my server is not acting as a open relay, i have spent like 2 months in this reading forums and i never got the answer to my problem i hope you can help me.

---

### Post by noway2 on 2009-09-16
Look in your mail log and see what is going on with the accounts that are sending that many emails.  It is probably in a file like /var/log/mail.log.  At the very least, that will show you to whom the emails are going and where / how they originated.

---

