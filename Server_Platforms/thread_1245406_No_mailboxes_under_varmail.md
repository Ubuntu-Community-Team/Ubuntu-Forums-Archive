---
title: "No mailboxes under /var/mail"
date: 2009-08-20
forum: Server Platforms
---

### Post by kschyff on 2009-08-20
Hello
 
I have just loaded and configured some of the basic settings to get postfix to work on ubuntu 9.0.4
 
I created a user called postmaster using the adduser command. after this i sent a mail message to postmaster from another account with mailx.
 
i typed:
 
[EMAIL="karl@vanderschyff:/var/mail$"]karl@vanderschyff:/var/mail$[/EMAIL] mail -s "hello there" [EMAIL="root@vanderschyff.net"]root@vanderschyff.net[/EMAIL]

after typing the message I went to /var/mail to lookup the message under the postmaster's mailbox, but I only see a directory for the user nobody.
 
what am i doing wrong that my users dont have mailboxes?
 
here is an extract of the /var/log/mail.log file
 
Aug 20 19:41:05 chimera postfix/pickup[30146]: 411E41B41A1: uid=1000 from=<karl>
Aug 20 19:41:05 chimera postfix/cleanup[30350]: 411E41B41A1: message-id=<[EMAIL="20090820174105.411E41B41A1@vanderschyff.net"]20090820174105.411E41B41A1@vanderschyff.net[/EMAIL]>
Aug 20 19:41:05 chimera postfix/qmgr[30149]: 411E41B41A1: from=<[EMAIL="karl@vanderschyff.net"]karl@vanderschyff.net[/EMAIL]>, size=332, nrcpt=1 (queue active)
Aug 20 19:41:05 chimera postfix/local[30352]: 411E41B41A1: to=<[EMAIL="root@vanderschyff.net"]root@vanderschyff.net[/EMAIL]>, orig_to=<[EMAIL="postmaster@vanderschyff.net"]postmaster@vanderschyff.net[/EMAIL]>, relay=local, delay=0.29, delay$
Aug 20 19:41:05 chimera postfix/qmgr[30149]: 411E41B41A1: removed

 
Please assist
 
Thanks
Karl

---

