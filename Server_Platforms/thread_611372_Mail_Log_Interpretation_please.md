---
title: "Mail Log Interpretation please"
date: 2007-11-12
forum: Server Platforms
---

### Post by charmcity on 2007-11-12
Hi and thanks for reading.

I was recently fortunate enough to have been hacked by the SSH attacks that are going around the web.  they were nice enough to use my IP to spam the world for a weekend and now I'm blacklisted and paranoid about letting it happen agian

I just re-installed linux (switched to ubuntu from suse) and got everything up and running.  I see a line in my mail log that looks concerning.   I have tested my server online it doesn't show as an open relay. -- but this entry looks like spam trying to relay. "kehl@argentummortgage.com>" is totally foreign to me and I am the only person on the box as of now.....  Can someone comment?

```
Nov 12 21:52:32 tommy postfix/qmgr[6161]: 72E482C0568: from=<>, size=3102, nrcpt=1 (queue active)
Nov 12 21:52:32 tommy postfix/smtp[7821]: 72E482C0568: host mx01.1and1.com[74.208.5.4] refused to talk to me: 550 RBL rejection: http://www.spamhaus.org/query/bl?ip=75.148.8.74
Nov 12 21:52:32 tommy postfix/smtp[7821]: 72E482C0568: to=<kehl@argentummortgage.com>, relay=mx00.1and1.com[74.208.5.3]:25, delay=3303, delays=3303/0.02/0.6/0, dsn=4.0.0, status=deferred (host mx00.1and1.com[74.208.5.3] refused to talk to me: 550 RBL rejection: http://www.spamhaus.org/query/bl?ip=75.148.8.74)
Nov 12 21:53:01 tommy cyrus/imap[6480]: open: user genesisma opened INBOX
Nov 12 21:54:05 tommy cyrus/master[5233]: process 6480 exited, status 0

```

---

### Post by HermanAB on 2007-11-12
Well, the important thing is that it was dropped after a Spamhaus RBL check.  You'll have to post your complete main.cf file if you want any analysis.

To test it, you can try doing a manual telnet mail session from another server (or another IP address on the same box that postfix hasn't glommed onto) and see how the setup behaves.  There are also some online services that will scan your box for you at the click of a mouse - some googling for "mail open relay online test" finds many, starting with abuseat right at the top of the list.

Then of course, be sure to scan all mail - incoming and outgoing - with Spamassassin, Clamav, DCC and Razor, plus Postgrey.  The combination will foil any spam attempt.

Cheers,

Herman

---

### Post by MJN on 2007-11-13
You should indeed be concerned given the surrounding circumstances. That log is saying Postfix had a message to post and the recipient server rejected it. The from line being <> suggests it's either spam or a automated reply regarding delivery (e.g. a failure).

Do you recognise the user genesisma? Whilst no guarantee it could could well have been sent by them given the similar timestamps (could easily be just coincidence though).

Check the deferred Postfix queue - look in /var/spool/Postfix/defer/ and see if there are any message sat in there.

Mathew

Edit: I've just done a quick test to check you're not an open relay (you're not) so unless you've changed the config recently it appears that the message in the log originated from your machine.

---

### Post by charmcity on 2007-11-13
Hi,

Thanks for the comments -- My main.cf is below.  I want to prevent ALL send traffic from my server (my users do not need to send from this host)

I am only interested in receiving mail at this location and having it delivered to Cyrus IMAP via LMTP.  It seems most of the mysterious traffic has stopped but I have still a couple of scary log items even today (I bold them below)  -- 

Main.cf
```
queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
mail_owner = postfix
myhostname = tommy.bostonst.com
mydomain = bostonst.com
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
unknown_local_recipient_reject_code = 550

mynetworks_style = host

mailbox_transport = lmtp:unix:/var/run/lmtp
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
debugger_command =
         PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
         xxgdb $daemon_directory/$process_name $process_id & sleep 5
sendmail_path = /usr/sbin/sendmail
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
setgid_group = postdrop
smtp_sasl_auth_enable = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain
smtpd_client_restrictions = permit_mynetworks, reject
smtpd_recipient_restrictions =
        permit_mynetworks,
        reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain

message_size_limit = 20000000

 
```


Scary Log Section from today (genesisma is ok, I most definitly don't send mail to Japan)
:
```
Nov 13 19:25:07 tommy cyrus/master[5234]: ready for work
Nov 13 19:25:07 tommy cyrus/master[5430]: about to exec /usr/sbin/ctl_cyrusdb
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: checkpointing cyrus databases
Nov 13 19:25:07 tommy cyrus/master[5431]: about to exec /usr/lib/cyrus/bin/notifyd
Nov 13 19:25:07 tommy cyrus/notify[5431]: executed
Nov 13 19:25:07 tommy postfix/master[5432]: daemon started -- version 2.4.5, configuration /etc/postfix
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: archiving database file: /var/lib/cyrus/annotations.db
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: archiving log file: /var/lib/cyrus/db/log.0000000001
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: archiving database file: /var/lib/cyrus/mailboxes.db
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: archiving log file: /var/lib/cyrus/db/log.0000000001
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: archiving log file: /var/lib/cyrus/db/log.0000000001
Nov 13 19:25:07 tommy cyrus/ctl_cyrusdb[5430]: done checkpointing cyrus databases
Nov 13 19:25:07 tommy cyrus/master[5234]: process 5430 exited, status 0
Nov 13 19:25:18 tommy postfix/master[5432]: reload configuration /etc/postfix

[B]
Nov 13 19:25:19 tommy postfix/qmgr[6168]: 45BB02C056A: from=<>, size=6190, nrcpt=1 (queue active)
Nov 13 19:25:20 tommy postfix/smtp[6177]: 45BB02C056A: host mail-fwdt.wh.ocn.ne.jp[122.1.231.79] refused to talk to me: 421 Server Temporarily unavailable
Nov 13 19:25:21 tommy postfix/smtp[6177]: 45BB02C056A: to=<jqxtvtngoo@takacho.com>, relay=mail-fwdt.wh.ocn.ne.jp[122.1.231.141]:25, delay=63293, delays=63291/1.1/0.82/0, dsn=4.0.0, status=deferred (host mail-fwdt.wh.ocn.ne.jp[122.1.231.141] refused to talk to me: 421 Server Temporarily unavailable)
[/B]

Nov 13 19:26:12 tommy postfix/pickup[6167]: 602202C056F: uid=1001 from=<genesisma>
Nov 13 19:26:12 tommy postfix/cleanup[6431]: 602202C056F: message-id=<20071114002612.602202C056F@tommy.bostonst.com>
Nov 13 19:26:12 tommy postfix/qmgr[6168]: 602202C056F: from=<genesisma@bostonst.com>, size=663, nrcpt=1 (queue active)
Nov 13 19:26:12 tommy postfix/local[6435]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Nov 13 19:26:12 tommy cyrus/master[6442]: about to exec /usr/lib/cyrus/bin/lmtpd
Nov 13 19:26:13 tommy cyrus/lmtpunix[6442]: executed
Nov 13 19:26:14 tommy cyrus/lmtpunix[6442]: accepted connection
Nov 13 19:26:14 tommy cyrus/lmtpunix[6442]: lmtp connection preauth'd as postman
Nov 13 19:26:14 tommy cyrus/lmtpunix[6442]: WARNING: sieve script /var/spool/sieve/g/genesisma/defaultbc doesn't exist: No such file or directory
Nov 13 19:26:14 tommy cyrus/lmtpunix[6442]: duplicate_check: <20071114002612.602202C056F@tommy.bostonst.com> user.genesisma       0
Nov 13 19:26:18 tommy cyrus/lmtpunix[6442]: duplicate_check: <20071114002612.602202C056F@tommy.bostonst.com> user.genesisma       0
Nov 13 19:26:18 tommy cyrus/lmtpunix[6442]: mystore: starting txn 2147483652
Nov 13 19:26:18 tommy cyrus/lmtpunix[6442]: mystore: committing txn 2147483652
Nov 13 19:26:18 tommy cyrus/lmtpunix[6442]: duplicate_mark: <20071114002612.602202C056F@tommy.bostonst.com> user.genesisma       1194999974 135568984
Nov 13 19:26:18 tommy cyrus/lmtpunix[6442]: Delivered: <20071114002612.602202C056F@tommy.bostonst.com> to mailbox: user.genesisma
Nov 13 19:26:18 tommy postfix/lmtp[6436]: 602202C056F: to=<genesisma@bostonst.com>, orig_to=<genesisma>, relay=tommy.bostonst.com[/var/run/lmtp], delay=12, delays=5.8/0.33/1.2/4.4, dsn=2.1.5, status=sent (250 2.1.5 Ok)
Nov 13 19:26:18 tommy postfix/qmgr[6168]: 602202C056F: removed
Nov 13 19:27:17 tommy cyrus/master[5234]: process 6442 exited, status 0

```

Thanks very much
Tom

---

### Post by MJN on 2007-11-14
Did you look in the deferred mail queue?
 
Messages in there will keep being attempted so they could be legacy message froms a while back - check to see if there are any and read 'em! (the headers will give you a clue where they originated from)
 
Mathew

---

