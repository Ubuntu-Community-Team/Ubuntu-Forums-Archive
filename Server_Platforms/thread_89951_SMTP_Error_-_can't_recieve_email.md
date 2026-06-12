---
title: "SMTP Error - can't recieve email"
date: 2005-11-13
forum: Server Platforms
---

### Post by Zelut on 2005-11-13
I've followed the instructions [here]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10") for setting up a server using Breezy 5.10.  This installs mySQL, apache, php, FTP, etc,etc & ISPConfig.  My problem is that I can email OUT of the box but not INTO the box.  Can anyone give me any ideas?  I appreciate it.

I get this error sent back to the original emailer

> Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 9): 553 sorry, relaying denied from your location

and this error in my /var/logs/mail.log:

> Nov 13 17:22:12 server1 courierpop3login: Connection, ip=[::ffff:127.0.0.1]
Nov 13 17:22:12 server1 postfix/smtpd[7492]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Nov 13 17:22:12 server1 postfix/smtpd[7492]: disconnect from localhost.localdomain[127.0.0.1]

---

