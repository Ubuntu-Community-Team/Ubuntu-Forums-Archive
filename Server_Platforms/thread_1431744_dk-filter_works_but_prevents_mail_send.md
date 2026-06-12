---
title: "dk-filter works but prevents mail send"
date: 2010-03-17
forum: Server Platforms
---

### Post by ernieg92 on 2010-03-17
I have searched several forums and have been unable to find an answer to this problem.

Using the Ubuntu Official/Community documentation, I set up a server (primarily mail/web).  Everything works great, except for one I have dk-filter running.  I can consistently produce the error.

1.  Postfix running as configured per [this instruction]("https://help.ubuntu.com/9.10/serverguide/C/postfix.html"). 

2.  Postfix mail filtering configured per [this instruction]("https://help.ubuntu.com/9.10/serverguide/C/mail-filtering.html").

3.  DomainKeys configured per [this instruction]("https://help.ubuntu.com/community/Postfix/DomainKeys").

4.  The server works fine if "dk-filter" is not running.  If I start "dk-filter" and send an email message, it gets stuck in the mail queue (log found below).  It will stay in the queue until I stop "dk-filter" and flush the queue.

5.  DKIM and DK are working, based on the testing/receptors I've used.  Sample output from dk.elandsys.com:
[LIST]
[*]DomainKeys Signature validation: pass (testing)
[*]DKIM Signature validation: pass (1024-bit key)
[/LIST]

Here are the log entries (between start and stop of dk-filter):
```


Mar 16 19:34:42 bluebird01 postfix/cleanup[11821]: BD4BD7AF: message-id=<4BA031B2.4070508@edge06.net>
Mar 16 19:34:47 bluebird01 postfix/qmgr[5307]: BD4BD7AF: from=<REDACTED>, size=1429, nrcpt=1 (queue active)
Mar 16 19:34:47 bluebird01 postfix/smtpd[11818]: disconnect from buford[192.168.0.1]
Mar 16 19:35:20 bluebird01 postfix/smtpd[11929]: connect from bluebird01[127.0.0.1]
Mar 16 19:35:20 bluebird01 postfix/smtpd[11929]: 2DC57CA6: client=bluebird01[127.0.0.1]
Mar 16 19:35:20 bluebird01 postfix/cleanup[11821]: 2DC57CA6: message-id=<4BA031B2.4070508@edge06.net>
Mar 16 19:35:25 bluebird01 dk-filter[11813]: 2DC57CA6: dk_eom(): resource unavailable: d2i_PUBKEY_bio() failed
Mar 16 19:35:25 bluebird01 dk-filter[11813]: 2DC57CA6 SSL error:0D06B08E:asn1 encoding routines:ASN1_D2I_READ_BIO:not enough data
Mar 16 19:35:25 bluebird01 postfix/cleanup[11821]: 2DC57CA6: milter-reject: END-OF-MESSAGE from bluebird01[127.0.0.1]: 4.7.1 Service unavailable - try again later; from=<REDACTED> to=<autorespond+dkim@dk.elandsys.com> proto=ESMTP helo=<localhost>
Mar 16 19:35:25 bluebird01 postfix/smtpd[11929]: disconnect from bluebird01[127.0.0.1]
Mar 16 19:35:25 bluebird01 amavis[9631]: (09631-10) Negative SMTP response to data-dot (<autorespond+dkim@dk.elandsys.com>): 451 4.7.1 Service unavailable - try again later
Mar 16 19:35:25 bluebird01 amavis[9631]: (09631-10) (!)FWD via SMTP: <REDACTED> -> <autorespond+dkim@dk.elandsys.com>,BODY=7BIT 451 4.7.1 TempFailed, id=09631-10, from MTA([127.0.0.1]:10025): 451 4.7.1 Service unavailable - try again later
Mar 16 19:35:25 bluebird01 amavis[9631]: (09631-10) Blocked MTA-BLOCKED, LOCAL [192.168.0.1] <REDACTED> -> <autorespond+dkim@dk.elandsys.com>, Message-ID: <4BA031B2.4070508@edge06.net>, mail_id: B3aIX84u6y+a, Hits: -2.357, size: 2025, 37344 ms
Mar 16 19:35:25 bluebird01 postfix/smtp[11822]: BD4BD7AF: to=<autorespond+dkim@dk.elandsys.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=43, delays=5.2/0.02/0.01/37, dsn=4.7.1, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.7.1 TempFailed, id=09631-10, from MTA([127.0.0.1]:10025): 451 4.7.1 Service unavailable - try again later (in reply to end of DATA command))

Mar 16 19:42:12 bluebird01 postfix/qmgr[5307]: BD4BD7AF: from=<REDACTED>, size=1429, nrcpt=1 (queue active)
Mar 16 19:42:32 bluebird01 postfix/smtpd[11984]: connect from bluebird01[127.0.0.1]
Mar 16 19:42:32 bluebird01 postfix/smtpd[11984]: 3C51BCA6: client=bluebird01[127.0.0.1]
Mar 16 19:42:32 bluebird01 postfix/cleanup[11977]: 3C51BCA6: message-id=<4BA031B2.4070508@edge06.net>
Mar 16 19:42:37 bluebird01 dk-filter[11813]: 3C51BCA6: dk_eom(): resource unavailable: d2i_PUBKEY_bio() failed
Mar 16 19:42:37 bluebird01 dk-filter[11813]: 3C51BCA6 SSL error:0D06B08E:asn1 encoding routines:ASN1_D2I_READ_BIO:not enough data
Mar 16 19:42:37 bluebird01 postfix/cleanup[11977]: 3C51BCA6: milter-reject: END-OF-MESSAGE from bluebird01[127.0.0.1]: 4.7.1 Service unavailable - try again later; from=<REDACTED> to=<autorespond+dkim@dk.elandsys.com> proto=ESMTP helo=<localhost>
Mar 16 19:42:37 bluebird01 postfix/smtpd[11984]: disconnect from bluebird01[127.0.0.1]
Mar 16 19:42:37 bluebird01 amavis[9631]: (09631-11) Negative SMTP response to data-dot (<autorespond+dkim@dk.elandsys.com>): 451 4.7.1 Service unavailable - try again later
Mar 16 19:42:37 bluebird01 amavis[9631]: (09631-11) (!)FWD via SMTP: <REDACTED> -> <autorespond+dkim@dk.elandsys.com>,BODY=7BIT 451 4.7.1 TempFailed, id=09631-11, from MTA([127.0.0.1]:10025): 451 4.7.1 Service unavailable - try again later
Mar 16 19:42:37 bluebird01 amavis[9631]: (09631-11) Blocked MTA-BLOCKED, LOCAL [192.168.0.1] <REDACTED> -> <autorespond+dkim@dk.elandsys.com>, Message-ID: <4BA031B2.4070508@edge06.net>, mail_id: b97cu8RoyiSw, Hits: -2.357, size: 2025, 25284 ms
Mar 16 19:42:37 bluebird01 postfix/smtp[11978]: BD4BD7AF: to=<autorespond+dkim@dk.elandsys.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=475, delays=449/0/0.01/25, dsn=4.7.1, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.7.1 TempFailed, id=09631-11, from MTA([127.0.0.1]:10025): 451 4.7.1 Service unavailable - try again later (in reply to end of DATA command))

Mar 16 22:02:24 bluebird01 postfix/cleanup[13725]: E4004C99: message-id=<4BA05450.20702@edge06.net>
Mar 16 22:02:30 bluebird01 postfix/qmgr[13711]: E4004C99: from=<REDACTED>, size=1393, nrcpt=1 (queue active)
Mar 16 22:02:30 bluebird01 postfix/smtpd[13720]: disconnect from buford[192.168.0.1]
Mar 16 22:03:02 bluebird01 postfix/smtpd[13730]: connect from bluebird01[127.0.0.1]
Mar 16 22:03:02 bluebird01 postfix/smtpd[13730]: 6333FC9E: client=bluebird01[127.0.0.1]
Mar 16 22:03:02 bluebird01 postfix/cleanup[13725]: 6333FC9E: message-id=<4BA05450.20702@edge06.net>
Mar 16 22:03:07 bluebird01 dk-filter[13715]: 6333FC9E: dk_eom(): resource unavailable: d2i_PUBKEY_bio() failed
Mar 16 22:03:07 bluebird01 dk-filter[13715]: 6333FC9E SSL error:0D06B08E:asn1 encoding routines:ASN1_D2I_READ_BIO:not enough data
Mar 16 22:03:07 bluebird01 postfix/cleanup[13725]: 6333FC9E: milter-reject: END-OF-MESSAGE from bluebird01[127.0.0.1]: 4.7.1 Service unavailable - try again later; from=<REDACTED> to=<autorespond+dk@dk.elandsys.com> proto=ESMTP helo=<localhost>
Mar 16 22:03:07 bluebird01 postfix/smtpd[13730]: disconnect from bluebird01[127.0.0.1]
Mar 16 22:03:07 bluebird01 amavis[13088]: (13088-02) Negative SMTP response to data-dot (<autorespond+dk@dk.elandsys.com>): 451 4.7.1 Service unavailable - try again later
Mar 16 22:03:07 bluebird01 amavis[13088]: (13088-02) (!)FWD via SMTP: <REDACTED> -> <autorespond+dk@dk.elandsys.com>,BODY=7BIT 451 4.7.1 TempFailed, id=13088-02, from MTA([127.0.0.1]:10025): 451 4.7.1 Service unavailable - try again later
Mar 16 22:03:07 bluebird01 amavis[13088]: (13088-02) Blocked MTA-BLOCKED, LOCAL [192.168.0.1] <REDACTED> -> <autorespond+dk@dk.elandsys.com>, Message-ID: <4BA05450.20702@edge06.net>, mail_id: KwXojAA3ncCY, Hits: -1.732, size: 1989, 37412 ms
Mar 16 22:03:07 bluebird01 postfix/smtp[13726]: E4004C99: to=<autorespond+dk@dk.elandsys.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=43, delays=5.3/0.02/0.01/37, dsn=4.7.1, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.7.1 TempFailed, id=13088-02, from MTA([127.0.0.1]:10025): 451 4.7.1 Service unavailable - try again later (in reply to end of DATA command))
```

Here are the applicable sections of dk-filter and Postfix's main.cf:

dk-filter:
```

DAEMON_OPTS="$DAEMON_OPTS -d edge06.net -s /etc/mail/dkim.key -S 2010"
SOCKET="inet:8892@localhost" # listen on loopback on port 8892
```

main.cf:
```

#Signing outgoing (DKIM) mail
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891,inet:localhost:8892
non_smtpd_milters = inet:localhost:8891,inet:localhost:8892
```

The domain is "edge06.net" if DNS record verification is necessary.

It has been nearly 36 hours since the DNS entries were created/updated, so I don't *think* that there is a resolution problem.

I can work without the dk-filter, but Yahoo has not moved over to DKIM yet.  Please help me figure this out.

Thanks!

---

