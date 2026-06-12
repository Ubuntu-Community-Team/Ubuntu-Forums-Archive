---
title: "Exim4 is not letting user login"
date: 2012-09-07
forum: Server Platforms
---

### Post by rohezal on 2012-09-07
I have setup a exim4 server with tls login, and dovecot for reading mails.

So far its working (for one user), I added a second user adv. Fetching mail is working but I cant send mails (with tls and without). 

Debian-exim is in the shadow group. Its using pam for authentification, for smtp and for imap. The adv user can login in imap using the same password as for stmp. Imap works, smtp does not work. Sometimes this message appears:

A TLS packet with unexpected length was received. I don't have plesk and no /etc/demouser.

Any ideas?

[12:18:26] SMTP< 220 PlaySavage2.com ESMTP Exim 4.71 Fri, 07 Sep 2012 12:18:26 +0200
domain name = alveran
[12:18:26] ESMTP> EHLO alveran
[12:18:26] ESMTP< 250-PlaySavage2.com Hello 
xxxx
[12:18:26] ESMTP< 250-SIZE 52428800
[12:18:26] ESMTP< 250-PIPELINING
[12:18:26] ESMTP< 250-AUTH PLAIN LOGIN CRAM-MD5
[12:18:26] ESMTP< 250-STARTTLS
[12:18:26] ESMTP< 250 HELP
[12:18:26] ESMTP> STARTTLS
[12:18:26] ESMTP< 220 TLS go ahead
SSL-Verbindung benutzt DHE-RSA-AES256-SHA
Server-Zertifikat:
  Betreff: /C=de/CN=playsavage2.com/emailAddress=***
  Aussteller(in): /C=de/CN=playsavage2.com/emailAddress=***
  SHA1 fingerprint: 87:97:4c:d0:e9:7c:14:68:43:51:43:38:b7:80:a0:c5:47:4c:42:3a
  MD5 fingerprint: e7:b2:c3:c1:8a:91:03:e9:6e:ce:f6:11:10:f1:78:d8
LibSylph-Message: SSL certificate of playsavage2.com previously accepted

[12:18:27] ESMTP> EHLO xxx
[12:18:27] ESMTP< 250-PlaySavage2.com Hello 
xxx
[12:18:27] ESMTP< 250-SIZE 52428800
[12:18:27] ESMTP< 250-PIPELINING
[12:18:27] ESMTP< 250-AUTH PLAIN LOGIN CRAM-MD5
[12:18:27] ESMTP< 250 HELP
[12:18:27] ESMTP> AUTH PLAIN ********
[12:18:27] ESMTP< 535 Incorrect authentication data


With the main user:

[12:24:46] SMTP< 220 PlaySavage2.com ESMTP Exim 4.71 Fri, 07 Sep 2012 12:24:46 +0200
[12:24:46] ESMTP> EHLO alveran
[12:24:46] ESMTP< 250-PlaySavage2.com Hello 
xxx
[12:24:46] ESMTP< 250-SIZE 52428800
[12:24:46] ESMTP< 250-PIPELINING
[12:24:46] ESMTP< 250-AUTH PLAIN LOGIN CRAM-MD5
[12:24:46] ESMTP< 250-STARTTLS
[12:24:46] ESMTP< 250 HELP
[12:24:46] ESMTP> STARTTLS
[12:24:46] ESMTP< 220 TLS go ahead
SSL-Verbindung benutzt DHE-RSA-AES256-SHA
Server-Zertifikat:
  Betreff: /C=de/CN=playsavage2.com/emailAddress=***
  Aussteller(in): /C=de/CN=playsavage2.com/emailAddress=***
  SHA1 fingerprint: 87:97:4c:d0:e9:7c:14:68:43:51:43:38:b7:80:a0:c5:47:4c:42:3a
  MD5 fingerprint: e7:b2:c3:c1:8a:91:03:e9:6e:ce:f6:11:10:f1:78:d8
LibSylph-Message: SSL certificate of playsavage2.com previously accepted

[12:24:46] ESMTP> EHLO alveran
[12:24:46] ESMTP< 250-PlaySavage2.com Hello 
xxx
[12:24:46] ESMTP< 250-SIZE 52428800
[12:24:46] ESMTP< 250-PIPELINING
[12:24:46] ESMTP< 250-AUTH PLAIN LOGIN CRAM-MD5
[12:24:46] ESMTP< 250 HELP
[12:24:46] ESMTP> AUTH PLAIN ********
[12:24:46] ESMTP< 235 Authentication succeeded
[12:24:46] SMTP> MAIL FROM:<***>
[12:24:46] SMTP< 250 OK
[12:24:46] SMTP> RCPT TO:<***>
[12:24:46] SMTP< 250 Accepted
[12:24:46] SMTP> DATA
[12:24:46] SMTP< 354 Enter message, ending with "." on a line by itself
[12:24:46] SMTP> . (EOM)
[12:24:46] SMTP< 250 OK id=1T9vjy-0000SX-Ne
[12:24:46] SMTP> QUIT
[12:24:46] SMTP< 221 PlaySavage2.com closing connection

---

### Post by rohezal on 2012-09-16
Just forgot to add the user in /etc/exim4/passwd

---

### Post by arwa99 on 2012-10-04
I have the same problem, 535 Incorrect authentication data.
I have added a file [FONT=Courier New]/etc/exim4/passwd[/FONT], but there are still problems.  but I do not know how to add the user and password in the / etc / passwd

[FONT=Courier New]/etc/exim4/passwd

[IMG]http://s16.postimage.org/qmc3mzyth/passwd.png[/IMG] 
/etc/passwd[/FONT]
[IMG]http://s10.postimage.org/j1vuvvoux/passwd2.png[/IMG]

---

