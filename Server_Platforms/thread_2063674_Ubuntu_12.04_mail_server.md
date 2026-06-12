---
title: "Ubuntu 12.04 mail server"
date: 2012-09-27
forum: Server Platforms
---

### Post by tangozopo on 2012-09-27
Hi good people,
Can you please assist me. l currently have a mail server that is running ubuntu 9.10. l have now installed ubuntu 12.04 on a new server but l am having problems setting up a mail server with the following features:
1.Postfix+Dovecot+Spamassassin+Clamav+Amavis+Horde
2.The server should use mbox (would be fine with maildir if its not a problem with horde)
3.Both incoming and outgoing mail should be scanned for spam as we have been blacklisted for spamming, outgoing mail should bounce back to the user in the local lan if spam is detected
My problem is with dovecot that seems to have been modularized and l can't see which modules in /etc/dovecot/conf.d/ which l can configure protocols i.e protoclos=pop3 imap...
The docs l have read so far seem to be talking about postfixadmin, mysql in dovecot files etc. l would be happy if someone can paste the configuration files with some explanation and also direct me to some sites with easy step by step guide. There seems to have been a lot of changes to the files l am used to.

Thanks in advance.

---

