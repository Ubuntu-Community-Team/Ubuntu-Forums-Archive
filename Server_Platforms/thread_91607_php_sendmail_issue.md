---
title: "php sendmail issue"
date: 2005-11-17
forum: Server Platforms
---

### Post by ytseshred on 2005-11-17
After upgrading to Breezy, I haven't been able to send mail using the mail() command in PHP anymore.  I was previously able to do so when running Warty.

I saw a good link in another thread which had a how-to to setup a mailserver, but that seemed to be a little more complex than what I need.

All I want to do is to be able to use the mail() command in php to send mail.  I don't care about receiving mail on that machine.

Can anyone start walking me through what I need to do to get sendmail working correctly?  Below are my system details, and what I've done:

Upgraded to Breezy
Upgraded to php5
Haven't had any other problems with any of my web apps since the upgrade.

If I try to use sendmail in the command line, just sending a simple message to my gmail address  (i.e., "sendmail [email]myaddress@gmail.com[/email]") typed a test message and then a '.' on a newline to send the message.  It never went through to my gmail account, and I didn't see any message in the /var/log/mail.log file.  

Any suggestions on where I should start?  Thanks

---

### Post by ytseshred on 2005-11-17
I actually just rechecked the /var/log/mail.log file, and this was what was in it, just in case it helps anyone diagnose the problem:

Nov 17 16:23:39 localhost postfix/master[6458]: fatal: /etc/postfix/master.cf: line 84: bad hostname or network address: ::1:smtp

Any ideas?

---

### Post by mattjriley on 2008-01-06
Hi,

I'm having a similar problem - did you manage to solve this in the end?

---

### Post by MJN on 2008-01-06
It sounds like you've lost IPv6 support. Commenting out that line would 'solve' it, but as for why IPv6 has hit the wall from just an upgrade I don't know.

Mathew

---

