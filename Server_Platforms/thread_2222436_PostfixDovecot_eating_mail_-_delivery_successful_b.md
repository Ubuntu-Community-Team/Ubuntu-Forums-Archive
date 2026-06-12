---
title: "Postfix/Dovecot eating mail - delivery successful but no file in Maildir"
date: 2014-05-06
forum: Server Platforms
---

### Post by christian20 on 2014-05-06
Hello,

I have a Ubuntu 14.04 server running Postfix 2.11 with Dovecot 2.2.9. There are several users on it which I use with virtual aliases to have several accounts with multiple domains. Everything worked fine until two days ago when mails delivered to my server got lost in a black hole (or hopefully something more earthly). I can't retrieve new mails via Evolution or Roundcube and there are no files in the Maildir newer than two days ago, but I can see that I received mails in the logs:

```
May  5 09:02:05 localhost postfix/pipe[14290]: A1138120065: to=<kontakt-christian@localhost>, orig_to=<***echte Adresse***>, relay=spamassassin, delay=5.1, delays=0.04/0/0/5, dsn=2.0.0, status=sent (delivered via spamassassin service)
May  5 09:02:05 localhost postfix/local[14297]: AD5AA12064A: to=<kontakt-christian@localhost>, relay=local, delay=0.01, delays=0/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
May  6 15:43:14 localhost postfix/pipe[2663]: CEACF120735: to=<kontakt-christian@localhost>, orig_to=<***echte Adresse***>, relay=spamassassin, delay=5.1, delays=0.05/0/0/5, dsn=2.0.0, status=sent (delivered via spamassassin service)
May  6 15:43:14 localhost postfix/local[2667]: DCFA1123593: to=<kontakt-christian@localhost>, relay=local, delay=0.01, delays=0/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
```

When I looked in mail.err, I discovered there were problems with Spamassassin, so I deactivated it. That was not helpful, I still don't actually retrieve mails though the log looks fine:

```
May 6 18:26:48 localhost postfix/smtpd[5462]: connect from mout.gmx.net[212.227.15.19]
May 6 18:26:48 localhost postfix/smtpd[5462]: 3A48B120BDC: client=mout.gmx.net[212.227.15.19]
May 6 18:26:48 localhost postfix/cleanup[5467]: 3A48B120BDC: message-id=<trinity-6d7c999d-635d-49aa-9490-ed9cb204d5b8-1399393607871@3capp-gmx-bs42>
May 6 18:26:48 localhost postfix/qmgr[5456]: 3A48B120BDC: from=<****>, size=1088, nrcpt=1 (queue active)
May 6 18:26:48 localhost postfix/local[5468]: 3A48B120BDC: to=<kontakt-christian@localhost>, orig_to=<***>, relay=local, delay=0.07, delays=0.06/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
May 6 18:26:48 localhost postfix/qmgr[5456]: 3A48B120BDC: removed
May 6 18:26:48 localhost postfix/smtpd[5462]: disconnect from mout.gmx.net[212.227.15.19]
```

It's no auth problem, I can login successfully, though I can't send mails either ("Relay access denied").

Access to the Maildir works fine; I also have a getmail setup that puts mails from external servers into some of my Maildir folders - those mails are retrieved by Evolution as usual. So there is something wrong between Postfix receiving mail from others and delivering that mail into my Maildir. I also have the impression mails are delivered to the correct account, as the shell notifies me of new mails when I log in, but I can't find it.

Below are my configs. Any help is appreciated!

Christian

main.cf:

```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = christian-gredig.de
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = 
smtpd_sasl_auth_enable = no
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = no
smtpd_recipient_restrictions = 
smtpd_sender_restrictions = 
mailbox_command = 
smtp_use_tls = no
smtpd_tls_received_header = no
smtpd_tls_mandatory_protocols = !SSLv2
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom
myorigin = /etc/mailname
inet_protocols = all
virtual_alias_domains = $myhostname, konzertheld.de, konzertheld.tk, flowing-it.de
virtual_alias_maps = hash:/etc/postfix/virtual
mydestination = localhost

```

master.cf:

```
smtp      inet  n       -       -       -       -       smtpdpickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp


showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache


maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}


uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)


ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
```

---

### Post by kosmokramer314 on 2014-05-06
This is a shot in the dark, but doesn't your setup require spam assassin to be running to deliver the email?  Can you turn spam assassin back on and adjust the settings to be a little more lax?  Maybe a list was updated that is causing the issue?

---

### Post by christian20 on 2014-05-06
I'm sorry. By "deactivating" Spamassassin I meant: remove it from the postfix conf. So it should no longer be relevant, except if I missed something (do you see something in the above posted config that is related to Spamassassin?). Good idea though, thanks!

---

### Post by kosmokramer314 on 2014-05-07
unfortunately no, but I'm not a whiz with email anyway..I just recently deployed my first mail server using the same tools so it was just an idea.  There may be something in this article that jogs your brain a bit..

[http://arstechnica.com/business/2014/03/taking-e-mail-back-part-3-fortifying-your-box-against-spammers/]("http://arstechnica.com/business/2014/03/taking-e-mail-back-part-3-fortifying-your-box-against-spammers/")

---

### Post by christian20 on 2014-05-07
I was able to get mails delivered to Maildir again by setting home_mailbox to "Maildir/". I have no idea why that is necessary now, it wasn't before.

Anyway, the more important question is: Where are the mails I should have retrieved meanwhile? They have to be *&#8203;somewhere.*

---

### Post by christian20 on 2014-05-07
The lost mail showed up in /var/mail in mbox format. I was able to download and restore them with Evolution. One of the mails contained my last aptitude update log which showed that mail-stack-delivery was removed. I have no idea why that happened but it propably caused the problems I had.

---

### Post by kosmokramer314 on 2014-05-08
nice find!  mark this as "solved" so others can use it for reference :)

---

