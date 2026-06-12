---
title: "SMTPS not responding"
date: 2009-05-03
forum: Server Platforms
---

### Post by Dy1anW on 2009-05-03
Yes, it's one of those Thunderbird -> Postfix problems, with a twist of SSL.

I can receive mail from the server just fine (IMAPS - port 993), but when sending I'm limited to port 25.  I get this error message from T-bird:

Sending of message failed.
The message could not be sent because connecting to SMTP server 192.168.1.10 failed.  The server may be unavailable or is refusing SMTP connections.  Pease verify that your SMTP server setting is correct and try again, or else contact your network administrator.

Checked to see if port 465 was even open:
465/tcp    open   smtps

Okay...  is it listening?
tcp     0     0     127.0.0.1:10025     0.0.0.0:*     LISTEN     5103/master
tcp     0     0     0.0.0.0:587            0.0.0.0:*     LISTEN     5103/master
tcp     0     0     0.0.0.0:465            0.0.0.0:*     LISTEN     5103/master
tcp     0     0     0.0.0.0:25              0.0.0.0:*     LISTEN     5103/master

Yup.  And 587 is another service (was part of amavis I think)

Can I connect?
Trying ::1...     (this reminds me to learn IPv6 one day)
Trying 127.0.0.1...
Connected to localhost
Escape character is '^]'.
Connection closed by foreign host.

Woah!  Don't even get to type anything?!  Anyone know what just happened?

---

### Post by Dy1anW on 2009-05-03
Just went through some config files with a 'fine tooth comb' and found some typos (my bad).  /usr/lib/sasl2/smtpd.conf was missing a colon after mech_list, and /etc/postfix/master.cf should have had smtpd (with space) removed in front of broken_sasl_auth_clients=yes.  That seemed to have *some* effect, in the sense that I don't get booted straight off when I telnet to 465, but even when I enter 'ehlo me', the daemon just waits...

and waits...  until I finally hit ^]

Any clues?



Maybe this will help:  from logs-
postfix/smtpd[28570]: SSL_accept error from my.domain[127.0.0.1]: -1

---

