---
title: "dpkg-reconfigure postfix buggy? postfix doesn't work. aliases.db?"
date: 2007-10-21
forum: Server Platforms
---

### Post by mrowth on 2007-10-21
Whenever I try **sudo dpkg-reconfigure postfix** I get as far as setting the local address extension character. 

Whether I leave it at "+", enter nothing, or enter "ªð3§=U)", I get a dialogue box saying: 

```
Bad recipient delimiter 
The recipient delimiter must be a single character. 'ok' is what you entered.
```

Or

```
The recipient delimiter must be a single character. 'backup' is what you entered.
```

when I hit "Cancel" instead of "Ok". It must be seeing the strings from the buttons instead of what was entered... Bug?

------

So... can I get this to work without dpkg-configure? 

Fresh Gutsy installation - 2 days old. I have to PCs (called earthworm and concertina) in a LAN behind a router connecting to an ADSL modem. I don't want to run a publically accessible mail server - only local users should be able to send mail (to each other or, possibly by relaying through my webhoster's mail server, to the rest of the Internet)

I already have a main.cf that used to work in Feisty. By now I've probably messed it up completely. Nothing ever arrives (or not where I could find it).

/var/logs/mail.err hits me with a whole slew of

```
Oct 21 21:18:03 earthworm postfix/smtpd[11233]: fatal: open database /etc/aliases.db: No such file or directory
Oct 21 21:18:18 earthworm postfix/local[11235]: fatal: open database /etc/aliases.db: No such file or directory
Oct 21 21:19:04 earthworm postfix/smtpd[11254]: fatal: open database /etc/aliases.db: No such file or directory
```

(earthworm is this machine here, ignoring the other for now - one step at a time)

/etc/postfix/main.cf - changes all the time, of course, but currently:

```
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu 7.10)

biff = no

append_dot_mydomain = no

#delay_warning_time = 4h

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

myhostname = earthworm
mydomain = localdomain

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain 
relayhost = insert-my-web-hoster-here.net
mynetworks = 127.0.0.0/8 192.168.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
```

Here's /var/mail.log recording an attempt to start postfix and then send a message, first through sendmail (seems to work from KMail's point of view, but where does it go?), then through local SMTP (remains in outbox until it times out or I stop postfix).

```
Oct 21 21:35:05 earthworm postfix/postfix-script[11629]: starting the Postfix mail system
Oct 21 21:35:05 earthworm postfix/master[11630]: daemon started -- version 2.4.5, configuration /etc/postfix
Oct 21 21:35:05 earthworm postfix/qmgr[11632]: B5CE6FFDA9: from=<mrowth@earthworm>, size=459, nrcpt=1 (queue active)
Oct 21 21:35:05 earthworm postfix/qmgr[11632]: B740BFFDCF: from=<mrowth@earthworm>, size=459, nrcpt=1 (queue active)
Oct 21 21:35:05 earthworm postfix/qmgr[11632]: BD5F0FFD2B: from=<mrowth@earthworm>, size=459, nrcpt=1 (queue active)
Oct 21 21:35:05 earthworm postfix/qmgr[11632]: D04F4FFDCE: from=<mrowth@earthworm>, size=459, nrcpt=1 (queue active)
Oct 21 21:35:05 earthworm postfix/qmgr[11632]: BA9A4FFDAA: from=<mrowth@earthworm>, size=457, nrcpt=1 (queue active)
Oct 21 21:35:05 earthworm postfix/qmgr[11632]: AAC47FFDCB: from=<mrowth@earthworm>, size=459, nrcpt=1 (queue active)
Oct 21 21:35:05 earthworm postfix/local[11634]: fatal: open database /etc/aliases.db: No such file or directory
Oct 21 21:35:06 earthworm postfix/master[11630]: warning: process /usr/lib/postfix/local pid 11634 exit status 1
Oct 21 21:35:06 earthworm postfix/master[11630]: warning: /usr/lib/postfix/local: bad command startup -- throttling
Oct 21 21:35:38 earthworm postfix/pickup[11631]: 8829CFFDD0: uid=1000 from=<mrowth@earthworm>
Oct 21 21:35:38 earthworm postfix/cleanup[11643]: 8829CFFDD0: message-id=<200710212135.38167.mrowth@earthworm>
Oct 21 21:35:38 earthworm postfix/qmgr[11632]: 8829CFFDD0: from=<mrowth@earthworm>, size=459, nrcpt=1 (queue active)
Oct 21 21:36:03 earthworm postfix/smtpd[11653]: fatal: open database /etc/aliases.db: No such file or directory
Oct 21 21:36:04 earthworm postfix/master[11630]: warning: process /usr/lib/postfix/smtpd pid 11653 exit status 1
Oct 21 21:36:04 earthworm postfix/master[11630]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 21 21:36:06 earthworm postfix/local[11655]: fatal: open database /etc/aliases.db: No such file or directory
Oct 21 21:36:07 earthworm postfix/master[11630]: warning: process /usr/lib/postfix/local pid 11655 exit status 1
Oct 21 21:36:07 earthworm postfix/master[11630]: warning: /usr/lib/postfix/local: bad command startup -- throttling
```

All messages from mrowth@earthworm (me @ where I'm sitting right now) to myself 

I don't know how to make an /etc/aliases.db - if that's what's needed here. 

In case it matters... fetchmail isn't fetching any mail, either.

I have a .fetchmailrc for several remote POP3 accounts, I can use fetchmail -c to check them, but no mail is retrieved. 

It's all a little confusing now.
Please help...

---

### Post by MJN on 2007-10-21
To create **/etc/aliases.db** you first need a **/etc/aliases** raw text file. It likely exists by default and will contain at least the mapping of who should get root's mail (e.g. **root: mathew** in my case). The file can then be converted into a  lookup table (with a .db extension) with [B]sudo postalias /etc/aliase

[/B]A **sudo newaliases** command will then be needed to be run (or restart Postfix) in order to make the new table take effect.

I'll wait before going through the rest of your config until you've tried it in case that's all that's wrong.

Mathew

P.S. Don't be tempted to add .db extensions to your alias* directives in main.cf - the extensions are assumed and adding them will throw it.

---

### Post by mrowth on 2007-10-21
> **MJN said:**
> To create **/etc/aliases.db** you first need a **/etc/aliases** raw text file. It likely exists by default and will contain at least the mapping of who should get root's mail (e.g. **root: mathew** in my case).
Yes, I've got that one.

>  The file can then be converted into a  lookup table (with a .db extension) with **sudo postmap /etc/aliases**
It says: 
```
postmap: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
```

**But** KMail then instantly received all the mail I had tried to send in addition to all the mail fetchmail'ed from my POP accounts.

> I'll wait before going through the rest of your config until you've tried it in case that's all that's wrong.

Looks like it, for now. 

Thank you! O:)

Though - I still can't send mail to "the greater Internet" although I've configured the right relayhost. 

```
Oct 21 22:57:11 earthworm postfix/smtpd[12220]: connect from ip6-localhost[::1]
Oct 21 22:57:11 earthworm postfix/smtpd[12220]: NOQUEUE: reject: RCPT from ip6-localhost[::1]: 554 5.7.1 <myname@freemailservice.com>: Relay access denied; from=<mrowth@earthworm> to=<myname@freemailservice.com> proto=ESMTP helo=<ip6-localhost>
Oct 21 22:57:11 earthworm postfix/smtpd[12220]: disconnect from ip6-localhost[::1]
```

That used to work before...

---

### Post by MJN on 2007-10-22
Since my initial response I changed **sudo postmap /etc/aliases **to **sudo postalias /etc/aliases**. I'm not sure what the difference is as in my mind they're doing the same job, but try that as it may work without the error.
 
For your 'relaying denied' problem this is most likely due to your current config, and your IPv6 localhost address in particular.
 
By default, unless you've specified otherwise, there is an **smtpd_recipient_restrictions** directive set to **permit_mynetworks, reject_unauth_destination**
 
You've specified **$mynetworks** as **127.0.0.0/8, 192.168.0.0/16** however you are currently connecting from **ipv6-localhost** hence you need to add this to the end of **$mynetworks** as **[::1]/128 **(giving **$mynetworks 127.0.0.0/8, 192.168.0.0/16, [::1]/128**)
 
Give that a shot.
 
Mathew

---

### Post by mrowth on 2007-10-25
Thanks again, that seems to have done the trick!

I'm a little confused, though (oh, really?!) - the lack of an ip6 IP in mynetworks didn't seem to matter when I sent mail to local users; it came through with no complaints:

Received: from <b>ip6-localhost (ip6-localhost [IPv6:::1])</b>
        by earthworm (Postfix) with ESMTP id 33C5C25ED04
        for <mrowth@earthworm>; (...)

I should probably rtfm...

---

### Post by mrowth on 2007-10-26
...

---

