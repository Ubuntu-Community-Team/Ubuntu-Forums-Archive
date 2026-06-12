---
title: "Postfix configuration problem..."
date: 2006-05-14
forum: Server Platforms
---

### Post by und3rtug4 on 2006-05-14
Hi there

I'm setting up my home mail server, and for that, i'm following this guide: [http://66.249.93.104/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1](http://66.249.93.104/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1)

.... that was mencioned here on the forum!

Everything went smooth, until i tried to telnet on port 25 to send a testing mail!

As mencioned on the guide, for testing purposes, we might wanna telnet mailserver 25, an i did it, and follow all the mencioned steps on the guide!

But something went wrong:

after the smtp banner i typed:

ehlo testing.org

and received the following output:

250-mail.bunk3r.org
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250-AUTH=LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250 8BITMIME

then i tryed the followin command:

mail from:<test@testing.org>

and instead of getting the 250-OK output, nothing append.....


It's my first time on mail server configuration, so i'm sorry if this is some dumb question, but i just dont know whats the problem!:confused: :confused: 

-------------------------------------------------------
Here is an extract of the /var/log/mail.log, hope it helps....
-------------------------------------------------------

May 14 20:54:30 localhost postfix/pickup[4891]: warning: maildrop/2B26B6AFB9: Error writing message file
May 14 20:54:30 localhost postfix/pickup[4891]: warning: 7199E6AFBF: message has been queued for 3420 days
May 14 20:54:30 localhost postfix/pickup[4891]: 7199E6AFBF: uid=0 from=<root>
May 14 20:54:30 localhost postfix/cleanup[4910]: warning: connect to mysql server 127.0.0.1: Host 'localhost.localdomain' is not allowed to connect to this MySQL server
May 14 20:54:30 localhost postfix/cleanup[4910]: warning: 7199E6AFBF: virtual_alias_maps map lookup problem for [email]root@bunk3r.org[/email]
May 14 20:54:30 localhost postfix/pickup[4891]: warning: maildrop/0F7376AFB1: Error writing message file
May 14 20:54:50 localhost postfix/trivial-rewrite[5027]: warning: connect to mysql server 127.0.0.1: Host 'localhost.localdomain' is not allowed to connect to this MySQL server
May 14 20:54:50 localhost postfix/trivial-rewrite[5027]: fatal: mysql:/etc/postfix/mysql-virtual_forwardings.cf(0,100): table lookup problem
May 14 20:54:51 localhost postfix/smtpd[5012]: warning: premature end-of-input on private/rewrite socket while reading input attribute name
May 14 20:54:51 localhost postfix/smtpd[5012]: warning: problem talking to service rewrite: Success
May 14 20:54:51 localhost postfix/master[4885]: warning: process /usr/lib/postfix/trivial-rewrite pid 5027 exit status 1
May 14 20:54:51 localhost postfix/master[4885]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
-----------------------------------------------------------------------

](*,)

---

### Post by und3rtug4 on 2006-05-14
Scenario Update:

After removing the localhost.localdomain entry from /etc/host, i finally got the 250-OK output. This problem was because the localhost.localdomain have no permission to access the mysql server.

Now i have a new problem:

After getting the 250-OK output from the mail from:<mail@somemail.org>, i typed rcpt to:<user@virtual.test>, and got the following output:

554 <user@virtual.test>: Relay access denied

.... Can anyone explain whats going on, and maybe suggest one possible solution?

Kind regards
und3rtug4

---

### Post by und3rtug4 on 2006-05-14
Scenario Update:

Possible solutions:
1 - Fix the "mynetworks=" field on /etc/postfix/main.cf
2 - Set the domain virtual.test as a virtual domain on the "mydestination=" field on /etc/postfix/main.cf


After several tests on the postfix main.cf configuration file on those two fields mencioned above, the "myneworks=" field was not the problem on this scenario. The 554 <user@virtual.test>: Relay access denied error, has been solve by adding the domain virtual.test to the "mydestination=" field on /etc/postfix/main.cf

Kindly
und3rtug4

---

