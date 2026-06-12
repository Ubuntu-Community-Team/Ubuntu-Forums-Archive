---
title: "Not receiving mail problem"
date: 2009-11-15
forum: Server Platforms
---

### Post by theRick on 2009-11-15
I am currently able to send mail on my server and can receive mail from one user to another - but I can not receive mail from external servers.

I have a couple different error results in mail.log ...

> Nov 16 02:55:12 printswell1 postfix/smtpd[4651]: connect from mail-fx0-f212.google.com[209.85.220.212]
Nov 16 02:55:12 printswell1 postfix-policyd: connection from: 127.0.0.1 port: 50518 slots: 0 of 4096 used
Nov 16 02:55:12 printswell1 postfix-policyd: rcpt=7, greylist=update, host=209.85.220.212 (mail-fx0-f212.google.com), from=rick_email@gmail.com, to=www@printswellphotos.com, size=0
Nov 16 02:55:12 printswell1 postfix-policyd: rcpt=7, throttle_rcpt=new(a), host=209.85.220.212, from=rick_email@gmail.com, to=www@printswellphotos.com, count=1/64(1), threshold=0%
Nov 16 02:55:12 printswell1 postfix/smtpd[4651]: 5D8DD18904: client=mail-fx0-f212.google.com[209.85.220.212]
Nov 16 02:55:13 printswell1 postfix/cleanup[4656]: 5D8DD18904: message-id=<aac0d0400911151848v42c562aarb1d8cdc83080e469@mail.gmail.com>
Nov 16 02:55:13 printswell1 postfix/qmgr[2833]: 5D8DD18904: from=<rick_email@gmail.com>, size=1871, nrcpt=1 (queue active)
Nov 16 02:55:13 printswell1 amavis[2364]: (02364-03) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: file(1) utility (/usr/bin/file) error: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3009, <GEN47> line 71. at (eval 102) line 193, <GEN47> line 71.
Nov 16 02:55:13 printswell1 amavis[2364]: (02364-03) (!)PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20091116T025513-02364
Nov 16 02:55:13 printswell1 postfix/smtp[4658]: 5D8DD18904: to=<www@printswellphotos.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.2, delays=0.96/0.01/0.12/0.12, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=02364-03, parts_decode_ext FAILED: file(1) utility (/usr/bin/file) error: run_command: can't fork: Cannot allocate memory at /usr/sbin/amavisd-new line 3009, <GEN47> line 71. at (eval 102) line 193, <GEN47> line 71. (in reply to end of DATA command))
Nov 16 02:55:43 printswell1 postfix/smtpd[4651]: disconnect from mail-fx0-f212.google.com[209.85.220.212]

And from a second address

> Nov 16 03:00:29 printswell1 postfix/smtpd[4699]: connect from mail-yx0-f187.google.com[209.85.210.187]
Nov 16 03:00:29 printswell1 postfix-policyd: connection from: 127.0.0.1 port: 35553 slots: 0 of 4096 used
Nov 16 03:00:29 printswell1 postfix-policyd: rcpt=8, greylist=new, host=209.85.210.187 (mail-yx0-f187.google.com), from=wife_email@gmail.com, to=images@printswellphotos.com, size=0
Nov 16 03:00:29 printswell1 postfix/smtpd[4699]: NOQUEUE: reject: RCPT from mail-yx0-f187.google.com[209.85.210.187]: 450 4.7.1 <images@printswellphotos.com>: Recipient address rejected: Policy Rejection- Please try later.; from=<wife_email@gmail.com> to=<images@printswellphotos.com> proto=ESMTP helo=<mail-yx0-f187.google.com>
Nov 16 03:00:29 printswell1 postfix/smtpd[4699]: disconnect from mail-yx0-f187.google.com[209.85.210.187]


The second looks like maybe its just a greylist issue, but I'm stumped on the top one.

Any help will be greatly appreciated.

---

### Post by theRick on 2009-11-15
Well I rebooted the server and the messages were then delivered.

I noticed that my swap file showed 0 free before the reboot and about 100mb free after the reboot so that likely played a role.

I'll keep an eye on it though to see if my swap file gets maxed out again.

---

