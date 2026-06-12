---
title: "Sendmail comcast relay question"
date: 2007-12-16
forum: Server Platforms
---

### Post by slijtan on 2007-12-16
So I had sendmail working from a ubuntu server @ home and all of a sudden it stopped working without me changing a thing.  I think it has to do with it trying to send from [email]root@comcast.net[/email], which is not a recognized email address?  The authentication seems to work fine, but I do get an error message in the log below that reads "550 5.1.0 Not our Customer".  I use the following command to try to send the email from the command line.  This command used to work a few weeks back, but it just randomly stopped working recently without me changing a thing:

sendmail -Am -v -t < test_email

test_email contains the following:
Date: Fri, 28 Sep 2007 11:28:32 -0700
Message-Id: <200709281828.l8SISWXg027022@server.hsd1.ca.comcast.net.>
From: [email]notify@lijen.dnsdojo.com[/email]
To: [email]lijentantan@gmail.com[/email]
Subject: Test Email
Mime-Version: 1.0
Content-Type: text/html

TEST!!


The resulting log reads:
[email]lijentan@gmail.com[/email]... Connecting to smtp.comcast.net port 587 via relay...
220 OMTA02.westchester.pa.mail.comcast.net comcast ESMTP server ready
>>> EHLO comcast.net.
250-OMTA02.westchester.pa.mail.comcast.net hello [98.207.98.195], pleased to meet you
250-HELP
250-AUTH LOGIN PLAIN CRAM-MD5
250-SIZE 15728640
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-STARTTLS
250 OK
>>> STARTTLS
220 2.0.0 Ready to start TLS
>>> EHLO comcast.net.
250-OMTA02.westchester.pa.mail.comcast.net hello [98.207.98.195], pleased to meet you
250-HELP
250-AUTH LOGIN PLAIN CRAM-MD5
250-SIZE 15728640
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 OK
>>> AUTH PLAIN Y2hhcmxlc3NoaWVoQGNvbWNhc3QubmV0AGNoYXJsZXNzaGllaEBjb21jYXN0Lm5ldABzb25nY2FrZQ==
235 2.7.0 ... authentication succeeded
>>> MAIL From:<root@comcast.net> SIZE=455 AUTH=root@comcast.net.
550 5.1.0 Not our Customer
root... aliased to lijen
/root/dead.letter... Saved message in /root/dead.letter
Closing connection to smtp.comcast.net
>>> QUIT
221 2.0.0 OMTA02.westchester.pa.mail.comcast.net comcast closing connection


Thanks in advance!

---

### Post by crouton on 2008-01-03
Seems like you are using Comcast as the SMTP smarthost, which is good.  However you are somehow sending as [email]root@comcast.net[/email], which is bad.

> I took me a little while to find the
masquerade_exceptions = root
value for /etc/postfix/main.cf to keep root's mail from leaving the node.

This is for postfix, which is the default in Ubuntu.  So check this file and see what is set.

---

