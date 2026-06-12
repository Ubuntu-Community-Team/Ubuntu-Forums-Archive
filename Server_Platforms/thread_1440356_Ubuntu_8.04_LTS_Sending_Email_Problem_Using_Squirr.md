---
title: "Ubuntu 8.04 LTS Sending Email Problem Using Squirrelmail / Dovecot"
date: 2010-03-27
forum: Server Platforms
---

### Post by merrydown on 2010-03-27
Hi, I am a server newbie and set up a server from scratch running a website for a client a few years ago which was my first ubuntu/linux experience.  I upgraded the ubuntu server recently to 8.04 LTS and sending emails no longer appears to work.  I get the error below (trying to send to my work email and a yahoo email account.

From what I can acertain it means that somewhere the configuration element specifying the domain the email is coming from has been lost.

The server uses dovecot and they are accessing their email using squirrelmail I set up on their server.

Can ANYONE help me with this, tell me where and how to fix this error, specify the domain or whatever?  Is the error likely to be in the config for squirrelmail, dovecot or something else?

Many,  many thanks to anyone who can try to help me with this...

Jim

-------------------------------------

The original message was received at Sat, 27 Mar 2010 16:00:22 GMT
from localhost [127.0.0.1]

   ----- The following addresses had permanent fatal errors -----
<jim@xxxxxxxxxx.co.uk>
    (reason: 501 <?? connection timed out? no servers could be reached>: Helo
command rejected: Invalid name)

   ----- Transcript of session follows -----
... while talking to mailserver.xxxxxxxxx.co.uk.:
>>> DATA
<<< 501 <?? connection timed out? no servers could be reached>: Helo command
rejected: Invalid name
554 5.0.0 Service unavailable
<<< 554 Error: no valid recipients
... while talking to a.mx.mail.yahoo.com.:
<<< 421 Message from (80.176.83.40) temporarily deferred - 4.16.50. Please refer to
[http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)
... while talking to e.mx.mail.yahoo.com.:
<<< 421 Message from (80.176.83.40) temporarily deferred - 4.16.50. Please refer to
[http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)
... while talking to c.mx.mail.yahoo.com.:
<<< 420 Resources unavailable temporarily. Please try later
(mta1061.mail.re4.yahoo.com)
... while talking to g.mx.mail.yahoo.com.:
<<< 421 Message from (80.176.83.40) temporarily deferred - 4.16.50. Please refer to
[http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)
... while talking to h.mx.mail.yahoo.com.:
<<< 421 Message from (80.176.83.40) temporarily deferred - 4.16.50. Please refer to
[http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)
... while talking to f.mx.mail.yahoo.com.:
<<< 421 Message from (80.176.83.40) temporarily deferred - 4.16.50. Please refer to
[http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)

---

