---
title: "postgrey running and in main.cf but not being used?"
date: 2012-11-23
forum: Server Platforms
---

### Post by troypiggo on 2012-11-23
G'day, I'm a bit puzzled.  I've installed postgrey on several servers before with no hassles, but on this new 12.04 install, I can see postgrey running, but incoming mails don't seem to be getting greylisted and are bypassing it by the looks.

Extract from /etc/postfix/main.cf:
```
smtpd_recipient_restrictions = permit_sasl_authenticated,
           permit_mynetworks,
           reject_unauth_destination,
           permit_dnswl_client list.dnswl.org,
           reject_rbl_client zen.spamhaus.org,
           reject_rbl_client bl.spamcop.net,
           check_policy_service inet:127.0.0.1:10023
```
Extract from /etc/default/postgrey:
```
POSTGREY_OPTS="--inet=10023"
```
```
Postgrey is running.  Extract from /var/log/mail.log:
Nov 24 13:29:20 mail postgrey[14678]: 2012/11/24-13:29:20 postgrey (type Net::Server::Multiplex) starting! pid(14678)
Nov 24 13:29:20 mail postgrey[14678]: Using default listen value of 128
Nov 24 13:29:20 mail postgrey[14678]: Binding to TCP port 10023 on host localhost#012
```
Something definitely listening on 10023:
```
# netcat -z -v localhost 10023
Connection to localhost 10023 port [tcp/*] succeeded!
```

Extract from /var/log/mail.log:
```
Nov 24 13:30:13 mail postfix/smtpd[15028]: connect from nskntmtas05p.mx.XYZ.com[61.9.168.149]
Nov 24 13:30:14 mail postfix/smtpd[15028]: 8B07956005E: client=nskntmtas05p.mx.XYZ.com[61.9.168.149]
Nov 24 13:30:14 mail postfix/cleanup[15044]: 8B07956005E: message-id=<20121124032840.GA3354@UVW.com.au>
Nov 24 13:30:14 mail postfix/qmgr[9944]: 8B07956005E: from=<troy@UVW.com.au>, size=1280, nrcpt=1 (queue active)
Nov 24 13:30:14 mail postfix/smtpd[15028]: disconnect from nskntmtas05p.mx.XYZ.com[61.9.168.149]
Nov 24 13:30:21 mail postfix/smtpd[15087]: connect from localhost[127.0.0.1]
Nov 24 13:30:21 mail postfix/smtpd[15087]: 92565560062: client=localhost[127.0.0.1]
Nov 24 13:30:21 mail postfix/cleanup[15044]: 92565560062: message-id=<20121124032840.GA3354@UVW.com.au>
Nov 24 13:30:21 mail postfix/qmgr[9944]: 92565560062: from=<troy@UVW.com.au>, size=1731, nrcpt=1 (queue active)
Nov 24 13:30:21 mail postfix/smtpd[15087]: disconnect from localhost[127.0.0.1]
Nov 24 13:30:21 mail amavis[1126]: (01126-04) Passed CLEAN, [61.9.168.149] [58.174.106.141] <troy@UVW.com.au> -> <troy@ABC.dyndns.org>, Message-ID: <20121124032840.GA3354@UVW.com.au>, mail_id: teUmz22wKCa5, Hits: 0.652, size: 1280, queued_as: 92565560062, 7004 ms
Nov 24 13:30:21 mail postfix/smtp[15045]: 8B07956005E: to=<troy@ABC.dyndns.org>, relay=127.0.0.1[127.0.0.1]:10024, delay=8.2, delays=1.2/0.01/0.02/7, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 92565560062)
Nov 24 13:30:21 mail postfix/qmgr[9944]: 8B07956005E: removed
Nov 24 13:30:21 mail postfix/local[15088]: 92565560062: to=<troy@ABC.dyndns.org>, relay=local, delay=0.16, delays=0.09/0.02/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Nov 24 13:30:21 mail postfix/qmgr[9944]: 92565560062: removed
Nov 24 13:33:34 mail postfix/anvil[15030]: statistics: max connection rate 1/60s for (smtp:61.9.168.149) at Nov 24 13:30:13
Nov 24 13:33:34 mail postfix/anvil[15030]: statistics: max connection count 1 for (smtp:61.9.168.149) at Nov 24 13:30:13
Nov 24 13:33:34 mail postfix/anvil[15030]: statistics: max cache size 1 at Nov 24 13:30:13

```

Anyone got any ideas on why mail appears to be bypassing it?

---

### Post by lisati on 2012-11-23
> **troypiggo said:**
> 

Anyone got any ideas on why mail appears to be bypassing it?
Possibly because 61.9.168.149 is listed in the dnswl list.

---

### Post by troypiggo on 2012-11-24
Aah, yes!  I removed the dnswl line in main.cf and postgrey did kick in.  Thanks mate!  Appreciate it.

---

