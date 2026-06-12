---
title: "Sendmail Config"
date: 2008-11-28
forum: Server Platforms
---

### Post by FiniteRed on 2008-11-28
Hi Everyone

I currently have a email server that use Dovecot and fetchmail, the inbound email works very well, however to send e-mail we (currenty) specify out ISP's SMTP - this can be very slow at times. I have been trying to configure sendmail so we can send email through our e-mail server as well as receive it, to test it I have tried to send mail from the command line, but get the following error:

Script to send command line email:

```
#!/usr/bin/perl
use Time::localtime;
open (OUT,"|/usr/sbin/sendmail -t -v");
print OUT "From: Administrator\@MyCompany.com\n";
print(OUT "Date: ".ctime()."\n");
print(OUT "To: FiniteRed\@MyCompany.com\n");
print(OUT "Subject: The subject\n");
print(OUT "\n");
print(OUT "Nobody\n");
close(OUT);
```

Resulting error:

```
FiniteRed@MyCompany.com... Connecting to [127.0.0.1] port 587 via relay...
220 myServer ESMTP Sendmail 8.14.2/8.14.2/Debian-2build1; Fri, 28 Nov 2008 10:46:49 GMT; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO myServer.gateway.2wire.net
250-myServer Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<administrator@myServer.gateway.2wire.net> SIZE=112 AUTH=administrator@myServer.gateway.2wire.net
250 2.1.0 <administrator@myServer.gateway.2wire.net>... Sender ok
>>> RCPT To:<FiniteRed@MyCompany.com>
>>> DATA
250 2.1.5 <FiniteRed@MyCompany.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <FiniteRed@MyCompany.com>... Connecting to MyCompany.com. via esmtp...
050 220-tompson.hostingzoom.com ESMTP Exim 4.69 #1 Fri, 28 Nov 2008 04:46:17 -0600 
050 220-We do not authorize the use of this system to transport unsolicited, 
050 220 and/or bulk e-mail.
050 >>> EHLO myServer
050 250-tompson.hostingzoom.com Hello myServer [81.149.79.134]
050 250-SIZE 52428800
050 250-PIPELINING
050 250-AUTH PLAIN LOGIN
050 250-STARTTLS
050 250 HELP
050 >>> STARTTLS
050 220 TLS go ahead
050 >>> EHLO myServer
050 250-tompson.hostingzoom.com Hello myServer [81.149.79.134]
050 250-SIZE 52428800
050 250-PIPELINING
050 250-AUTH PLAIN LOGIN
050 250 HELP
050 >>> MAIL From:<administrator@myServer.gateway.2wire.net> SIZE=326 AUTH=<>
050 250 OK
050 >>> RCPT To:<FiniteRed@MyCompany.com>
050 >>> DATA
050 550-Verification failed for <administrator@myServer.gateway.2wire.net>
050 550-The mail server could not deliver mail to administrator@myServer.gateway.2wire.net.  The account or domain may not exist, they may be blacklisted, or missing the proper dns entries.
050 550 Sender verify failed
050 503-All RCPT commands were rejected with this error:
050 503-Sender verify failed
050 503 Valid RCPT command must precede DATA
050 >>> RSET
050 250 Reset OK
050 <administrator@myServer.gateway.2wire.net>... Connecting to local...
050 <administrator@myServer.gateway.2wire.net>... Sent
250 2.0.0 mASAknS4006588 Message accepted for delivery
FiniteRed@MyCompany.com... Sent (mASAknS4006588 Message accepted for delivery)
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 myServer closing connection
```

Can anyone give me a hand in fixing this problem?

Cheers

FR

---

### Post by MJN on 2008-11-28
I would suggest installing Postfix instead. The time it will take to roll back what you have already done will be made up by the savings made in the future given the much simpler, yet equally powerful, configuration.
 
(It may also be worth you explaining where the Exim server fits in - you didn't mention it in your setup description however it appears in the SMTP transcript)
 
Mathew

---

### Post by hictio on 2008-11-28
Does "myServer.gateway.2wire.net" have a FQDN?
Does "myServer.gateway.2wire.net" have accept email? That is, if your server doesn't, is there a valid MX entry "myServer.gateway.2wire.net"?

Another thing, you can send emails from the CLI thru Sendmail like this:

```

/usr/sbin/sendmail -t -v user@server.something -s "Your Subject"

```

Type your email, and to send it (and see the output of the connection) type Ctrl + D

---

