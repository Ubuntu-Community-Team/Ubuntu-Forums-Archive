---
title: "Mail server set up"
date: 2012-03-01
forum: Server Platforms
---

### Post by deepakdeshp on 2012-03-01
1. I want to send mails outside the domain from my Ubuntu 10.04 server .I want to set up mail server on Ubuntu server 10.04 so that mysql is used as the database and I can get mails into Thunderbird client using the mail server. Should I use dovecot,postfix? I have tried it but its not working. 


Here is the problem output

Envelope-to: [EMAIL="nagios@ubuntu.tejas"]nagios@ubuntu.tejas[/EMAIL]
Delivery-date: Tue, 14 Feb 2012 01:43:27 -0500
Date: Tue, 14 Feb 2012 01:43:27 -0500
X-Failed-Recipients: [EMAIL="shwetaka@gmail.com"]shwetaka@gmail.com[/EMAIL]
Auto-Submitted: auto-replied
From: Mail Delivery System <Mailer-Daemon@ubuntu.tejas>
To: [EMAIL="nagios@ubuntu.tejas"]nagios@ubuntu.tejas[/EMAIL]
Subject: Mail delivery failed: returning message to sender
X-UID: 2861

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [EMAIL="shwetaka@gmail.com"]shwetaka@gmail.com[/EMAIL]
    **Mailing to remote domains not supported**


[http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid](http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid)

2. I have a registered domain at panchakarmaa.com . Using its mail server how can I send mails from my Ubuntu server/client?

3. Since I have registered another domain but am not having any web space for it.  Can I use this for my mail server set up on my ubuntu server and using it can I send mai outside the domain to google.com and yahoo.com?

---

