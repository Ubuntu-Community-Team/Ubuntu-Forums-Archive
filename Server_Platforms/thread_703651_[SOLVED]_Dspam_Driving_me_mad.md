---
title: "[SOLVED] Dspam Driving me mad"
date: 2008-02-21
forum: Server Platforms
---

### Post by Stephen_at on 2008-02-21
I'm moving over from an old Suse 9.0 server to a Ubuntu 6.x server.

DSPAM is driving me mad. I'm using it in daemon mode and I've set it so that the dspam.sock is in /var/spool/postfix/tmp

as can be seen by an ls -l

srwxrwxrwx 1 root dspam 0 Feb 21 19:29 dspam.sock

but postqueue -p

reports:

[FONT="Courier New"]-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
B23695DCB33      558 Thu Feb 21 18:52:54  [email]steve@xx.yyy.xx[/email]
(connect to /var/spool/postfix/tmp/dspam.sock[/var/spool/postfix/tmp/dspam.sock]: No such file or directory)
                                         [/FONT]

and mail.info shows:

[FONT="Courier New"]status=deferred (connect to /var/spool/postfix/tmp/dspam.sock[/var/spool/postfix/tmp/dspam.sock]: No such file or directory)
[/FONT]

and this is what I have in my master.cf:


[FONT="Courier New"]
smtp      inet  n       -       -       -       -       smtpd -o content_filter=lmtp:unix:/var/spool/postfix/tmp/dspam.sock
dspam   unix    n       -       -       -       10      pipe
 flags=Ru user=dspam argv=/usr/bin/dspam --deliver=innocent --user dspam -i -f $sender -- $recipient
dspam-retrain   unix    n       -       -       -       10      pipe
  flags=Ru user=dspam argv=/usr/bin/dspam-retrain $nexthop $sender $recipient
localhost:10026 inet  n -       -       -       -        smtpd
  -o content_filter=
  -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
  -o smtpd_helo_restrictions=
  -o smtpd_client_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject
  -o mynetworks=127.0.0.0/8
  -o smtpd_authorized_xforward_hosts=127.0.0.0/8

[/FONT]

and this is the config for the dpsam daemon:

[FONT="Courier New"]DeliveryHost        127.0.0.1
DeliveryPort        10026
DeliveryIdent       localhost
[/FONT]

There are no spaces in the dpam.sock name on my server so have no idea why this forum has inserted them!

I installed dspam from the repository and had to change a few permissions because they were wrong
On Suse I compiled it from scratch and it works perfectly.

No doubt I've done something silly but I can't see it

---

### Post by Stephen_at on 2008-02-22
Its the damned socket path in the postfix file. As its all running in /var/spool/postfix you need to leave it off the path in the postfix conf but leave it on in the dspam.conf.

So I did that and then go not history because dpsam writes its log files and of course the webfui can't read them as by default the files are written with rsther restricted rights.

Oh well. Its working now!

---

### Post by jelle-e on 2008-02-25
> **Stephen_at said:**
> 
[FONT="Courier New"]
smtp      inet  n       -       -       -       -       smtpd -o content_filter=lmtp:unix:/var/spool/postfix/tmp/dspam.sock
[/FONT]


If you state it with a "n" at the third line, it won't be chroot'ed and the path will start at "/" and not the "/chroot-path".

smtp      inet  n       -       n       -       -       smtpd -o ...

---

