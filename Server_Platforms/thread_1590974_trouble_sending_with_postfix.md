---
title: "trouble sending with postfix"
date: 2010-10-08
forum: Server Platforms
---

### Post by spankmeister7 on 2010-10-08
Hi.

I'm trying to get my linux box to send emails to me for general notification purposes. It's a remote server. All I want to do is to get an SMTP server installed. I've read some how-tos on Postfix, and I've installed it without issue.

I can test it via telnet, but when I go to send a message I get this in the /var/log/mail.log file:

Oct  7 01:27:42 somecomputer postfix/postfix-script[13678]: the Postfix mail system is not running                         
Oct  7 01:38:49 somecomputer postfix/postfix-script[13778]: starting the Postfix mail system                               
Oct  7 01:38:49 somecomputer postfix/master[13780]: fatal: bind 0.0.0.0 port 25: Address already in use                    
Oct  7 01:38:56 somecomputer postfix/postfix-script[13788]: the Postfix mail system is not running                         
Oct  7 04:28:21 somecomputer postfix/postdrop[13910]: warning: unable to look up public/pickup: No such file or directory  
Oct  8 19:36:22 somecomputer sm-mta[19059]: o98JXru7019059: SYSERR(root): collect: Cannot write ./dfo98JXru7019059 (bfcommi
t, uid=0, gid=108): No such file or directory                                                                           
Oct  8 19:36:22 somecomputer sm-mta[19059]: o98JXru7019059: from=<root@localhost>, size=15, class=0, nrcpts=1, proto=ESMTP,
 daemon=MTA-v4, relay=localhost [127.0.0.1] 

I've search the forums and found similar things, but no answers. The funny part is that I tested out the exact same install on my home linux box and it worked without issue. Both systems are running up-to-date Ubuntu 10.4 LTS.

Thanks for any help.

-m.

---

### Post by spankmeister7 on 2010-10-08
Solved my own problem.

Sendmail was installed, but I don't remember installing it.

I removed it and now all is well.

Thanks for reading.

---

