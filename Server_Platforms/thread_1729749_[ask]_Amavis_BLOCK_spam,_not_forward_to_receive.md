---
title: "[ask] Amavis BLOCK spam, not forward to receive"
date: 2011-04-15
forum: Server Platforms
---

### Post by venol on 2011-04-15
hello, I follow tutorial from [http://serion.co.nz/content/howto-setup-mailserver-using-postfix-mysql-dovecot-postfixadmin-amavis-new](http://serion.co.nz/content/howto-setup-mailserver-using-postfix-mysql-dovecot-postfixadmin-amavis-new)  But for email contains spam is not working properly. Amavis detect spam, but not forward to the receive. I set "final_spam_destination = D_PASS", but spam BLOCKED by amavis. 

what's problem..
thanks..

---

### Post by venol on 2011-04-16
need help .

---

### Post by falko on 2011-04-16
Any errors in your mail log?

---

### Post by venol on 2011-04-16
thanks for reply. Log on my server like this . .

> 
Apr 11 15:32:00 mail postfix/pickup[3376]: 4185621A16: uid=1000 from=<venol>
Apr 11 15:32:00 mail postfix/cleanup[3817]: 4185621A16: message-id=<20110411083200.GA3806@indra.com>
Apr 11 15:32:00 mail postfix/qmgr[3377]: 4185621A16: from=<venol@localhost>, size=1240, nrcpt=1 (queue active)
Apr 11 15:32:02 mail amavis[3774]: (03774-01) Blocked SPAM, <venol@localhost> -> <guest@indra.com>, quarantine: v/spam-vs9ZxfjgcD+i.gz, Message-ID: <20110411083200.GA3806@indra.com>, mail_id: vs9ZxfjgcD+i, Hits: 999.999, size: 1240, 2604 ms
Apr 11 15:32:02 mail postfix/smtp[3819]: 4185621A16: to=<guest@indra.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=2.7, delays=0.06/0.02/0.04/2.6, dsn=2.7.0, status=sent (250 2.7.0 Ok, discarded, id=03774-01 - SPAM)
Apr 11 15:32:02 mail postfix/qmgr[3377]: 4185621A16: removed

what's problem?
thanks.

---

### Post by venol on 2011-04-17
maybe someone can help me.
;)

---

