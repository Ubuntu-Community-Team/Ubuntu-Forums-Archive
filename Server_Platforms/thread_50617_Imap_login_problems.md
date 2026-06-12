---
title: "Imap login problems"
date: 2005-07-20
forum: Server Platforms
---

### Post by caeserjk on 2005-07-20
I followed this guide : [http://www.ubuntuforums.org/showthread.php?t=40047&highlight=courier](http://www.ubuntuforums.org/showthread.php?t=40047&highlight=courier)

to setup an email server using postfix, courier-imap, mysql for authentication. I am able to recieve email and have it drop into the proper maildir's but cant login in to the imap service. 

If I : telnet localhost 143 I get the chance to login to the imap server. But when I try with a user located in the users table of the maildb database it fails. For example:

ab login user password
ab NO Login failed.


Any suggestions.

---

### Post by GTvulse on 2005-07-20
Courier defaults to asking for user names of the form <user>@<domain>. If you don't have a domain name set up properly, in files, DNS, NIS, anything, Courier-IMAP may be dropping the connections on the floor. Have you tried using Dovecott IMAP instead?

---

### Post by LordHunter317 on 2005-07-21
[QUOTE=dradul]Courier defaults to asking for user names of the form <user>@<domain>.[/quote]No, it doesn't, by default.  However for virtual domains, it is likely that it is.

To the OP:  Your configuration would be quite useful and helpful.  Unfortunately, the guide you followed is excessively more complicated than necessary, and has some other (mostly minor) issues.

---

