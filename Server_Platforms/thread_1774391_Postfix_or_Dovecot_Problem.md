---
title: "Postfix or Dovecot Problem"
date: 2011-06-03
forum: Server Platforms
---

### Post by Jay89 on 2011-06-03
Hello, I have a Ubuntu 10.0.4 server 64-bit email server. I have installed Postfix and Dovecot. I've been working on it the past few days, dealing with problems as they come up. My latest one seems to be a domain issue. And I'm lost as to why this isn't working since I already added it to a test domain. (I hope I did at least). 

[U]IN /VAR/LOG:
[/U]Jun  3 08:27:01 newmail postfix/pickup[3792]: 50B0319C1E64: uid=0 from=<root>
Jun  3 08:27:01 newmail postfix/cleanup[4040]: 50B0319C1E64: message-id=<20110603122701.50B0319C1E64@newmail.testdegc.net>
Jun  3 08:27:01 newmail postfix/qmgr[3793]: 50B0319C1E64: from=<root@newmail.testdegc.net>, size=346, nrcpt=1 (queue active)
**Jun  3 08:27:16 newmail postfix/smtp[4041]: 50B0319C1E64: to=<testit@testdegc.net>, relay=none, delay=15, delays=0.11/0.12/15/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=testdegc.net type=AAAA: Host not found)**
Jun  3 08:27:16 newmail postfix/cleanup[4040]: 8C06E19C1F72: message-id=<20110603122716.8C06E19C1F72@newmail.testdegc.net>
Jun  3 08:27:16 newmail postfix/bounce[4047]: 50B0319C1E64: sender non-delivery notification: 8C06E19C1F72
Jun  3 08:27:16 newmail postfix/qmgr[3793]: 8C06E19C1F72: from=<>, size=2304, nrcpt=1 (queue active)
Jun  3 08:27:16 newmail postfix/qmgr[3793]: 50B0319C1E64: removed
Jun  3 08:27:16 newmail dovecot: deliver(degcit): msgid=<20110603122716.8C06E19C1F72@newmail.testdegc.net>: saved mail to INBOX
Jun  3 08:27:16 newmail postfix/local[4048]: 8C06E19C1F72: to=<degcit@newmail.testdegc.net>, orig_to=<root@newmail.testdegc.net>, relay=local, delay=0.16, delays=0.06/0.01/0/0.1, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  3 08:27:16 newmail postfix/qmgr[3793]: 8C06E19C1F72: removed

If you need my dovecot or postfix configuration please let me know.

THANKS!

---

### Post by tapi0n on 2011-06-03
Could you give a little more info? Like some configs (dovecot and postfix)?

edit: Could this possible be a dns problem?

---

### Post by SeijiSensei on 2011-06-03
> Name service error for name=testdegc.net type=AAAA: Host not found

There's no such domain as testdegc.net.  A whois lookup for that name returns nothing.

Unless you have a private nameserver of your own that provides DNS for that domain name, you won't be able to send mail there.  Also this is an IPv6 DNS error (the "type=AAAA" indicates that).  Are you using IPv6?

---

### Post by Jay89 on 2011-06-03
Thanks for your reply. No, this isn't an ipv6 network. But I will take a look at our private name server and post a reply. But while we are on that subject. Why would it assume to be ipv6? I never configured it to do so.

---

### Post by Jay89 on 2011-06-06
I looked in the dns server and mapped 10.X.X.X to newmail.domain.net and verified with the nslookup and ping commands. But Mail still returns with the same error. On a side note.. How can I make sure the domain name on the server is indeed changed? Because in /var/log it still shows the old domain name as part of the recipient's address even though I changed the /etc/hosts file and resolv.conf.[COLOR=Navy]
[/COLOR]

---

### Post by Jay89 on 2011-06-07
Okay, I figured out this particular problem. I didn't realize there was a /etc/mailname file that still had the old domain name.. But now I have a new one:

[COLOR=Navy][B]Jun  7 14:08:43 newmail postfix/pickup[1760]: B26DE19C0BF6: uid=0 from=<root>
Jun  7 14:08:43 newmail postfix/cleanup[2099]: B26DE19C0BF6: message-id=<20110607180843.B26DE19C0BF6@newmail.test.net>
Jun  7 14:08:43 newmail postfix/qmgr[1761]: B26DE19C0BF6: from=<root@newmail.test.net>, size=342, nrcpt=1 (queue active)
Jun  7 14:08:43 newmail postfix/cleanup[2099]: C342219C0AAE: message-id=<20110607180843.B26DE19C0BF6@newmail.test.net>
Jun  7 14:08:43 newmail postfix/local[2101]: B26DE19C0BF6: to=<fakeuser@localhost>, relay=local, delay=0.17, delays=0.1/0.01/0/0.06, dsn=2.0.0, status=sent (forwarded as C342219C0AAE)
Jun  7 14:08:43 newmail postfix/qmgr[1761]: C342219C0AAE: from=<root@newmail.test.net>, size=477, nrcpt=1 (queue active)
Jun  7 14:08:43 newmail postfix/qmgr[1761]: B26DE19C0BF6: removed
Jun  7 14:08:43 newmail postfix/smtp[2102]: C342219C0AAE: to=<fakeuser@test.net>, orig_to=<fakeuser@localhost>, relay=test.net[10.1.0.11]:25, delay=0.17, delays=0.06/0.01/0/0.1, dsn=5.7.1, status=bounced (host test.net[10.1.0.11] said: 550 5.7.1 Unable to relay for [EMAIL="fakeuser@degreec.net"]fakeuser@test.net[/EMAIL] (in reply to RCPT TO command))
Jun  7 14:08:43 newmail postfix/cleanup[2099]: ECC5A19C0C05: message-id=<20110607180843.ECC5A19C0C05@newmail.test.net>
Jun  7 14:08:44 newmail postfix/bounce[2103]: C342219C0AAE: sender non-delivery notification: ECC5A19C0C05
Jun  7 14:08:44 newmail postfix/qmgr[1761]: ECC5A19C0C05: from=<>, size=2504, nrcpt=1 (queue active)
Jun  7 14:08:44 newmail postfix/qmgr[1761]: C342219C0AAE: removed
Jun  7 14:08:44 newmail postfix/cleanup[2099]: 06FFA19C0AAE: message-id=<20110607180843.ECC5A19C0C05@newmail.test.net>
Jun  7 14:08:44 newmail postfix/local[2101]: ECC5A19C0C05: to=<root@newmail.test.net>, relay=local, delay=0.09, delays=0.06/0/0/0.03, dsn=2.0.0, status=sent (forwarded as 06FFA19C0AAE)
Jun  7 14:08:44 newmail postfix/qmgr[1761]: 06FFA19C0AAE: from=<>, size=2645, nrcpt=1 (queue active)
Jun  7 14:08:44 newmail postfix/qmgr[1761]: ECC5A19C0C05: removed
Jun  7 14:08:44 newmail postfix/smtp[2102]: 06FFA19C0AAE: to=<fakeuser@test.net>, orig_to=<root@newmail.test.net>, relay=test.net[10.1.0.13]:25, delay=0.12, delays=0.03/0/0/0.08, dsn=5.7.1, status=bounced (host test.net[10.1.0.13] said: 550 5.7.1 Unable to relay for [EMAIL="fakeuser@degreec.net"]fakeuser@test.net[/EMAIL] (in reply to RCPT TO command))
Jun  7 14:08:44 newmail postfix/qmgr[1761]: 06FFA19C0AAE: removed[/B][/COLOR]

Any ideas?

---

### Post by Jay89 on 2011-06-07
Once again never mind haha. I was missing the **relay_domains **command and something in the **mydestinations** command.

---

