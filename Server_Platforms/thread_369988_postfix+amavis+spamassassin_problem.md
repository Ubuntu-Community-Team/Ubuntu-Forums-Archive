---
title: "postfix+amavis+spamassassin problem"
date: 2007-02-25
forum: Server Platforms
---

### Post by cammj on 2007-02-25
im having a problem with my postfix+amavis+sa configuration. 

sa is reporting mail as spam when i run it using the spamassassin command on a raw mail message.. by running the command

spamassassin -D < /path/to/raw/mail

it reports that there is enough points to consider the email spam.

but the messages that go through postfix arnt being passed to spamassassin.. 

theres a message in /var/log/mail.log showing that its passing through amavis and being reported as clean.

---

### Post by Mr. C. on 2007-02-25
Its best to show the evidence.  Show log entries, obsfucate addresses and IPs as necessary.

There are several possibilities, but a primary one is that you are running spamassassin via command line as a user different that amavis, thus different bayes databases, etc.

Show the scores presented in both situations and compare the results.

---

### Post by cammj on 2007-02-25
mail.log

Feb 26 07:47:04 x postfix/smtpd[5732]: connect from localhost[127.0.0.1]
Feb 26 07:47:04 x postfix/smtpd[5732]: 2828B2DC839: client=localhost[127.0.0.1]
Feb 26 07:47:04 x postfix/cleanup[5727]: 2828B2DC839: message-id=<45E1FD04.2060901@x.org>
Feb 26 07:47:04 x amavis[4001]: (04001-04) Passed CLEAN, [x] [x] <cam@x.org> -> <cam@x.org>, Message-ID: <45E1FD04.2060901@x.org>, mail_id: W8u-cprqDb2w, Hits: 1.989, 1182 ms
Feb 26 07:47:04 x postfix/smtpd[5732]: disconnect from localhost[127.0.0.1]
Feb 26 07:47:04 x postfix/smtp[5728]: CE3D52DC6CF: to=<cam@x.org>, relay=127.0.0.1[127.0.0.1], delay=2, status=sent (250 2.6.0 Ok, id=04001-04, from MTA([127.0.0.1]:10025): 250 Ok: queued as 2828B2DC839)
Feb 26 07:47:04 x postfix/virtual[5733]: 2828B2DC839: to=<cam@x.org>, relay=virtual, delay=0, status=sent (delivered to maildir)


spamassassin -D < 1172438224.V301I2e4d95M268584.x.org.org:2, result

Content analysis details:   (5.7 points, 5.0 required)

 pts rule name              description
---- ---------------------- --------------------------------------------------
 1.7 SARE_MLB_Stock6        BODY: ML obfuscated ticker symbols
 1.7 SARE_PROLOSTOCK_SYM3   BODY: Last week's hot stock scam
 0.0 HTML_MESSAGE           BODY: HTML included in message
 0.0 MIME_HTML_ONLY         BODY: Message only has text/html MIME parts
 2.0 RCVD_IN_SORBS_DUL      RBL: SORBS: sent directly from dynamic IP address
                            [x listed in dnsbl.sorbs.net]
 0.4 AWL                    AWL: From: address is in the auto white-list

---

### Post by Mr. C. on 2007-02-25
Ok, we can see that amavis is scoring at 1.989, but your command line run of spamassassin is scoring at above 5.  And there is no way those scores could be combined to total 1.989.

I'm presuming when you ran spamassassin, you did not run at as the amavis user, as in:

sudo -H -u amavis spamassassin ...

This is important.  Try re-running the it again, this time using as the amavis user.

To see why amavis is getting different scores, you can increase the log_level in amavisd.conf to 2:

$log_level = 2;

restart amavis, and observe the scores shown in the log.  Look for SPAM-TAG lines.

You can also set

$sa_tag_level_deflt  = -10.0;

to include the headers in each message that identify which rules and scores are being assigned to a mail message.

See if this helps.  If not, next steps will be to run amavis with debug-sa.

MrC

---

