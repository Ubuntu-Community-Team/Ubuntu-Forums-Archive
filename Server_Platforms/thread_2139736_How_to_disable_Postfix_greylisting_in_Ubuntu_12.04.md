---
title: "How to disable Postfix greylisting in Ubuntu 12.04 LTS server ?"
date: 2013-04-27
forum: Server Platforms
---

### Post by dchen on 2013-04-27
Currently running an Ubuntu 12.04 LTS server with postfix/dovecot/spamassassin/squirrelmail mail server.

The reason we want to disable the greylisting in Postfix was because the mail server can't received the mail if the sender
and the sender's domain and the recipient is the first time to the receiving mail server, the mail will be put in the greylist for
later retry, this caused tremendous delay or sometime we never got that mail if the sender didn't re-send the mail.

I googled a bit, and found that other version of Ubuntu such as 10.4.2 LTS can disable the Postfix Policy greylisting by
specifying the following line in the /etc/postfix-policyd.conf file:
GREYLISTING=0
However, in 12.04 LTS server there is NO such /etc/postfix-policyd.conf file !

Any help or insights will be greatly appreciated.  thx.

---

### Post by nerdtron on 2013-06-26
Greylisting is in the file /etc/cluebringer/cluebringer.conf

---

