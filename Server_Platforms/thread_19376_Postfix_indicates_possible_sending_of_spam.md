---
title: "Postfix indicates possible sending of spam?"
date: 2005-03-11
forum: Server Platforms
---

### Post by theantix on 2005-03-11
I recently upgraded my mail server to Ubuntu using Postfix, and I've noticed a bunch of odd activity in the /var/log/mail.info file.  Here is an example of what I'm talking about, showing the progression of a single message over time in my server logs:
----
ryan@serv0r:~ $ grep -i '458c23c2ce' /var/log/mail.info
Mar 11 07:44:35 localhost postfix/qmgr[31654]: 458C23C2CE: from=<>, size=2999, nrcpt=1 (queue active)
Mar 11 07:44:35 localhost postfix/smtp[18910]: 458C23C2CE: to=<amw1224@altavista.net>, relay=none, delay=156586, status=deferred (Name service error for name=altavista.net type=MX: Malformed name server reply)
Mar 11 08:51:15 localhost postfix/qmgr[31654]: 458C23C2CE: from=<>, size=2999, nrcpt=1 (queue active)
Mar 11 08:51:19 localhost postfix/smtp[19326]: 458C23C2CE: to=<amw1224@altavista.net>, relay=none, delay=160590, status=deferred (Name service error for name=altavista.net type=MX: Malformed name server reply)
Mar 11 10:14:35 localhost postfix/qmgr[31654]: 458C23C2CE: from=<>, size=2999, nrcpt=1 (queue active)
Mar 11 10:14:35 localhost postfix/smtp[20246]: 458C23C2CE: to=<amw1224@altavista.net>, relay=none, delay=165586, status=deferred (Name service error for name=altavista.net type=MX: Malformed name server reply)
Mar 11 11:21:15 localhost postfix/qmgr[31654]: 458C23C2CE: from=<>, size=2999, nrcpt=1 (queue active)
Mar 11 11:21:19 localhost postfix/smtp[21030]: 458C23C2CE: to=<amw1224@altavista.net>, relay=none, delay=169590, status=deferred (Name service error for name=altavista.net type=MX: Malformed name server reply)
Mar 11 12:44:35 localhost postfix/qmgr[31654]: 458C23C2CE: from=<>, size=2999, nrcpt=1 (queue active)
Mar 11 12:44:36 localhost postfix/smtp[22198]: 458C23C2CE: to=<amw1224@altavista.net>, relay=none, delay=174587, status=deferred (Name service error for name=altavista.net type=MX: Malformed name server reply)
Mar 11 13:53:07 localhost postfix/qmgr[22351]: 458C23C2CE: from=<>, size=2999, nrcpt=1 (queue active)
Mar 11 13:53:11 localhost postfix/smtp[23133]: 458C23C2CE: to=<amw1224@altavista.net>, relay=none, delay=178702, status=deferred (Name service error for name=altavista.net type=MX: Malformed name server reply)
---

I've confirmed that my server is not acting as an open relay by checking out the configuration on abuse.net -- but these messages baffle me.  There are many of them, all going to seemingly bogus users and all having an empty "from=<>" indicator instead of the legitimately sent ones which have legitimate "from=<mylocaluser@mylocaldomain.com>".  I am worried that I am accidentally sending out spam to the world and would like to prevent this from happening if possible... please help!

I'm new to postfix and can't figure out what to do next from their documentation.  I'm looking to do the following:
(A)  figure out how to turn on the logging so I can find out what the orgins of these suspect emails is.
(B)  prevent sending messages with blank "from=<>" messages
(C)  if the problem is with a mailer hole in a PHP/perl application, to figure out how to block the www-data user from sending mail from these apps but still allow my legitimate Horde setup to send mail.
(D)  finally, if there is anything obvious I am missing.  I am new to postfix so I'm open to any suggestions or tips a more experienced user might be able to share with me.

Cheers,
-rt-

---

### Post by alastair on 2005-03-11
Why don't you have a look at the message?

find /var/spool/postfix/defer* -name "458C23C2CE"

---

### Post by theantix on 2005-03-11
[QUOTE=alastair]Why don't you have a look at the message?

find /var/spool/postfix/defer* -name "458C23C2CE"[/QUOTE]

Thank you very much -- looking at the first few of those messages showed me what they were -- they were in fact the result of spam sent to an invalid account on my machine and these log messages were of the bounces were going back to the various domains.  And then failing, as so often happens.  Anyhow -- thanks for showing me how to debug postfix a bit better, knowing how postfix stores mail like that will help me in other areas as well.  Have a great day!

Cheers,
-rt-

---

### Post by alastair on 2005-03-11
Great - good to see it helped.

Postfix is actually a great mail server. The web site has good information/docs :

[http://www.postfix.org](http://www.postfix.org)

Also, the postfix mailing list is VERY good. But, before asking questions there. read the docs/faq and check the list for the right information to offer.

---

