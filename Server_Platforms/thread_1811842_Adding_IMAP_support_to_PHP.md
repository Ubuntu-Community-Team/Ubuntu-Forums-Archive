---
title: "Adding IMAP support to PHP"
date: 2011-07-25
forum: Server Platforms
---

### Post by Madman6510 on 2011-07-25
I'm testing a support ticketing system (osTicket), and am trying to set up the server so it can send and receive messages using an external email account so it will, you know, work.

When you try to add an email account, it spits out the error "IMAP doesn't exist. PHP must be compiled with IMAP enabled." in the web interface.

So apparently IMAP isn't enabled in PHP. And apparently I have to recompile PHP to add that particular function. Um... how i do that? i not so good with computer...

Running Ubuntu Server 11.04 x64.

---

### Post by Wayne_V on 2011-07-25
try 'apt-get install php5-imap'

---

### Post by ma13129926 on 2012-10-26
read this bro:

[http://drupalhigh.onsugar.com/phps-imap-functions-2188455](http://drupalhigh.onsugar.com/phps-imap-functions-2188455)

=D

it works for me =P

---

