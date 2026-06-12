---
title: "postfix sasl"
date: 2005-05-09
forum: Server Platforms
---

### Post by lee_connell on 2005-05-09
Hey all,

I've built an email server using postfix postfix-tls sasl2 cyrus using shadow as the auth method using plain as the mech.

I've got cyrus authenticating and storing emails properly, i got postfix accepting mail, delivering it and sending fine.

My problem is when i'm outside of the permit_mynetworks rule I'm trying to use permit_sasl_authentication and it keeps telling me "relay access denied".  I've made user /etc/shadow had read writes for the proper group.  testsaslauthd does complete with OK.  I do know also that postfix is running chrooted by default in debian, however i took that off by putting an n under chroot and when i run the /etc/init.d/postfix start script, it seems to think it's still running chrooted.  Could this be the problem or is it something else that I could be misssing.

I've turned on -v logging for postfix in master.cf and it doesn't tell me much still.  I am sure I am missing something but I am so aggrivated that the logs are not more descriptive of what the heck the problem is so I can just fix this problem and move on.

Any help is GREATLY appreciated!!!

Thanks,

Lee

P.S.  attached are my configs.

---

### Post by lee_connell on 2005-05-09
Ok looks like i got further debugging going on here.  The problem is the email client cannot start an authentication process let alone a EHLO command.  This is the response i get from connecting to the postfix server from outside of the domain.  Even the banner is screwed up looking.

220 *******************************
EHLO ammocomp.com
502 Error: command not implemented
ehlo ammocomp.com
502 Error: command not implemented
auth plain
502 Error: command not implemented
mail from:
501 Syntax: MAIL FROM: <address>
mail from: [email]lee@quality.com[/email]
250 Ok
rcpt to: [email]lee@ammo.com[/email]
554 <lee@ammo.com>: Relay access denied

Here is the response i get when im inside the network, same domain.

mail:/usr/local/lib# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mail ESMTP Postfix (Debian/GNU)
ehlo ammo.com
250-mail
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-AUTH PLAIN
250 8BITMIME
auth plain *****xlZQBsY29ubm*****
235 Authentication successful
mail from: [email]lee@quality.com[/email]
250 Ok
rcpt to: [email]lee@ammo.com[/email]
250 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
testing my email
.
250 Ok: queued as A281F24014

quit
221 Bye
Connection closed by foreign host.

Why is it being retarded when i'm not on the network?

---

### Post by lee_connell on 2005-05-09
Hey all,

The reason for this happening is becuase the server is behind a cisco firewall/router which is using the smtp fixup feature by default which is causing this behavior.  You just need to disable this and it will work.

Thanks

---

### Post by lee_connell on 2005-05-09
Also your mechs have to be "plain login" for outlook and outlook express to work, only thunderbird worked with just plain

---

