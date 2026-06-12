---
title: "dovecot-postfix SSL certificates, guru needed"
date: 2010-04-30
forum: Server Platforms
---

### Post by pksings on 2010-04-30
I keep getting the following errors.

Apr 30 09:36:01 phred dovecot: imap-login: Fatal: Can't load private key file /etc/ssl/private/ssl-mail.key: Key is for a different cert than /etc/ssl/certs/ssl-mail.pem


I'm stumped. I have removed all traces of dovecot using synaptic and even deleted all of the directories including /var/backups/dovecot-postfix/. I also deleted /etc/ssl/private/ssl-mail.key and /etc/ssl/certs/ssl-mail.pem before re-installing. Both reappeared after the install and give me the same error.

Today I removed everything I could find that anything to do with postfix and dovecot.
apt-get remove dovecot-postfix mailscanner mailutils postfix  rkhunter dovecot-common dovecot-antispam libmailutils2.

Then I ran searches in /usr, /var, /etc, and /lib for dovecot* and postfix* and deleted all of them. 
I then deleted  /etc/ssl/private/ssl-mail.key and /etc/ssl/certs/ssl-mail.pem. 

Then I re-installed everything.
apt-get install dovecot-postfix mailscanner mailutils postfix rkhunter dovecot-common dovecot-antispam libmailutils2

And I got the exact same error.....  

I've been at this for three days and nothing has worked. I need a guru, any available?   Next step is format a reload everything, this is so Window$.

Thanks in advance..

I have solved this by removing openssl, postfix, dovecot and a bunch of other stuff, deleting all trace of them and re-installing them. The keys were regenerated and now work fine, dovecot installed itself per the documentation and postfix config was restored from backup, working fine now.



PK

---

