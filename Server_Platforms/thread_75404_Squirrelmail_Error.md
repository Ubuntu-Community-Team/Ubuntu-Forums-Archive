---
title: "Squirrelmail Error"
date: 2005-10-13
forum: Server Platforms
---

### Post by dcostelloe on 2005-10-13
Hi All,
Just did an upgrade on my server and since the re-install I get the following error from Squirrelmail:
ERROR:
ERROR : Connection dropped by imap-server.

The config reports: Congratulations, your SquirrelMail setup looks fine to me!

I checked all the logs and things are ok mail is comming in a being placed in the mailboxes. Mysql log reports everything ok.

The following in the mail.info

Oct 13 17:14:04 localhost imaplogin: authdaemon: ACCEPT, username [email]myemail@mydomain.com[/email]
Oct 13 17:14:04 localhost imaplogin: LOCKED, user=myemail@mydomain.com, ip=[::ffff:127.0.0.1]

I can't see anything wrong?

When I telnet thigs are ok mail get received etc

:rolleyes:

---

