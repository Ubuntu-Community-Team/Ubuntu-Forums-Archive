---
title: "exim4 and TLS"
date: 2013-05-11
forum: Server Platforms
---

### Post by clearski on 2013-05-11
Hello, everyone!

I run exim4 server on 127.0.0.1 (test.com) and I successfully installed and tested TLS and SASL.

```
swaks -a -tls -q AUTH -s test.com -au test_user

=== Trying test.com:25...
=== Connected to test.com.
<-  220 test.com ESMTP Exim 4.80 Sat, 11 May 2013 10:34:59 +0300
 -> EHLO test.com
<-  250-test.com Hello localhost [127.0.0.1]
<-  250-SIZE 52428800
<-  250-8BITMIME
<-  250-PIPELINING
<-  250-STARTTLS
<-  250 HELP
 -> STARTTLS
<-  220 TLS go ahead
=== TLS started w/ cipher DHE-RSA-AES256-SHA
=== TLS peer subject DN="/CN=test.com/emailAddress=test_user@test.com"
 ~> EHLO test.com
<~  250-test.com Hello localhost [127.0.0.1]
<~  250-SIZE 52428800
<~  250-8BITMIME
<~  250-PIPELINING
<~  250-AUTH PLAIN
<~  250 HELP
 ~> AUTH PLAIN AGl0Z3V5AE41MDZCMTA1MTIwNjI=
<~  235 Authentication succeeded
 ~> QUIT
<~  221 test.com closing connection
=== Connection closed with remote host.
```

Everything looks good so far, at least that's what I'd like to believe. :) But everytime I send a message it doesn't want to use TLS, it's just doing the regular stuff.

```

tail -3 /var/log/exim4/mainlog

2013-05-11 10:35:36 1Ub4LA-0001cY-Od <= test_user@test.com U=test_user P=local S=449
2013-05-11 10:35:36 1Ub4LA-0001cY-Od => test_user <test_user@test.com> R=local_user T=mail_spool
2013-05-11 10:35:36 1Ub4LA-0001cY-Od Completed
```

My passwd file is */etc/exim4/passwd.client*:

```
test.com:test_user:secretpassword
```

*Mailx* isn't asking for any password and isn't using any password.

Is there any way to use TLS for all local connections?

Thank you.

Thank you.

---

### Post by clearski on 2013-05-11
I got it working with Thunderbird.

```
mailx
Heirloom mailx version 12.5 6/20/10.  Type ? for help.
"/var/mail/testuser": 1 message 1 new
>N  1 testuser              Sat May 11 18:52   25/787   Test
? 
Message  1:
From testuser@test.com Sat May 11 18:52:27 2013
Return-path: <testuser@test.com>
Envelope-to: testuser@test.com
Delivery-date: Sat, 11 May 2013 18:52:27 +0300
Date: Sat, 11 May 2013 18:52:27 +0300
From: testuser <testuser@test.com>
User-Agent: Mozilla/5.0 (X11; Linux i686; rv:17.0) Gecko/20130404 Thunderbird/17.0.5
To: testuser@test.com
Subject: Test
Content-Type: text/plain; charset=ISO-8859-1; format=flowed
Status: R

If you read this, it works.
```

And the log file:

```
testuser@test:~$ cat /var/log/exim4/mainlog 
2013-05-11 18:52:27 [6418] SMTP connection from [127.0.0.1]:55900 I=[127.0.0.1]:465 (TCP/IP connection count = 1)
2013-05-11 18:52:27 [7034] 1UbC5z-0001pS-6Z <= testuser@test.com H=(test.com) [127.0.0.1]:55900 I=[127.0.0.1]:465 P=esmtpsa X=TLS1.0:DHE_RSA_CAMELLIA_256_CBC_SHA1:256 CV=no SNI="test.com" A=plain_saslauthd_server:testuser S=633 id=518E693B.506@test.com from <testuser@test.com> for testuser@test.com
2013-05-11 18:52:27 [7034] SMTP connection from (test.com) [127.0.0.1]:55900 I=[127.0.0.1]:465 closed by QUIT
2013-05-11 18:52:27 [7036] 1UbC5z-0001pS-6Z => testuser <testuser@test.com> F=<testuser@test.com> P=<testuser@test.com> R=local_user T=mail_spool S=787 QT=0s DT=0s
2013-05-11 18:52:27 [7036] 1UbC5z-0001pS-6Z Completed QT=0s
```

But there's one thing I don't like. *testuser* is using the same password for email and system login. The only way I got smtp working was providing the password for the user account, not the password from /etc/exim4/passwd.client file, which was rejected. Is it possible to use different passwords?

---

