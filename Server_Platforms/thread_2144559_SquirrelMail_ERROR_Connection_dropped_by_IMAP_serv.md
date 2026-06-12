---
title: "SquirrelMail ERROR: Connection dropped by IMAP server"
date: 2013-05-12
forum: Server Platforms
---

### Post by CatorAde on 2013-05-12
hi guys,

after following many tutorials these last couple of days, i followed one suggested by a member in here, and all seemed to be going well until the last stage where it asked me to log into SquirrelMail, the Error i get is :-ERROR: Connection dropped by IMAP server

im guessing everything is installed correctly but maybe a configuration needs tweaking? has anyone come across this problem, or know how to fix it?

many thanks
Ade

---

### Post by snathan99 on 2013-05-13
Did you check /var/log/mail.*?

Also depending on whether you use dovecot, courier, etc, things may change.

Check apace logs as well

Here is another link to setup mail server: [http://tech.snathan.org/tech/linux/mail_server_setup](http://tech.snathan.org/tech/linux/mail_server_setup)

Mostly the issue may be outside of squirrelmail itself. Are you able to receive/send mail via a different client?

There is a squirrelmail debug plugin you can try. I have not used it myself.

Hope it helps - in essence a lot more information is required before this can be resolved.

---

### Post by SeijiSensei on 2013-05-13
Did you run conf.pl to configure SquirrelMail?  If so, run it again to make sure that the IMAP server information is correct.

---

