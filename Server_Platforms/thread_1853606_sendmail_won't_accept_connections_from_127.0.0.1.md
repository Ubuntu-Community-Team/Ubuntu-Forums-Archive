---
title: "sendmail won't accept connections from 127.0.0.1"
date: 2011-10-02
forum: Server Platforms
---

### Post by chazz_tsc on 2011-10-02
Running Ubuntu 10.04LTS. Sendmail is running, I have a number of different clients on it and mail transfers quite well from everywhere except localhost.

The operative log line reads, in part:
  To: [EMAIL="info@mydomain.com"]info@mydomain.com[/EMAIL], ctladdr=www-data (33/33), ... mailer-relay, relay=[127.0.0.1] [127.0.0.1], stat=Deferred, Connection refused by [127.0.0.1]

I've sanitized mydomain.com, it is a TLD that I own and the MX record in DNS points to my server. I'm trying to send using the mail call in PHP from Apache, and there are no logged errors in the apache logs.

It's tempting to suggest that this issue started when I started requiring STARTTLS for SMTP, but the problem is longstanding; I don't get logwatch digests, haven't since long before the STARTTLS code was put in place, and an examination of the logs indicates that they are also being punted for the same reason 

to: postmaster...
to: smmsp...
to: root, ctladdr=smmsp...

Operative lines in sendmail.mc:
```
DAEMON_OPTIONS(`Name=MTA,Address=10.2.1.105')dnl
DAEMON_OPTIONS=(`Name=MTALocal,Address=127.0.0.1')dnl
DAEMON_OPTIONS=(`Name=MSA,Port=987,Modifiers=E')dnl
```My firewall is set to redirect port 25 on the publicly routable address to 10.2.1.105, and that is working... it must be, because the address forum mail is sent to is on that server, and I must have gotten that else I wouldn't be able to post.

Any ideas?

---

### Post by chazz_tsc on 2011-10-02
Never mind...

looks like it just took a while before it noticed a mailer daemon running on 127.0.0.1. Now dumping an overwhelming backlog of mail -- dovecot apparently can't keep up.

---

