---
title: "Sending email from local server"
date: 2018-01-11
forum: Server Platforms
---

### Post by petervulky on 2018-01-11
Hello.
Please advise. I need to set up a postfix or anything else to (only) send email from my local server (and others if needed) . Postfix I configured to send via external SMTP with login data. Email will be sent to SMTP server, but SMTP server blocks it because it can not verify the sender. And of course it can not be email is from a localhost.
App SendEmail works, but I have to write all the data including the command: server smtp, the name and the password.
Postfix had it in conf. but it does not work.
How do I set "FROM" to ?header? email to send when I type in the terminal:
echo "This is a test." | mail -s Testing [email]myreal@email.com[/email]

Please, help me.

---

### Post by LHammonds on 2018-01-11
If your SMTP server allows relays, you could add your local server's IP address to your SMTP server's allowed relay server list.  Then you could send emails to it without validation.

LHammonds

---

### Post by TheFu on 2018-01-12
There is a post somewhere in these forums for using gmail servers to send email from Linux.   I couldn't find it, but didn't look too hard.

[https://www.howtoforge.com/tutorial/configure-postfix-to-use-gmail-as-a-mail-relay/](https://www.howtoforge.com/tutorial/configure-postfix-to-use-gmail-as-a-mail-relay/) isn't for ubuntu, but postfix is postfix. Besides the package manager stuff, the conf files and restart/reload should be the same.

Found this: [https://ubuntuforums.org/showthread.php?t=1711217](https://ubuntuforums.org/showthread.php?t=1711217) - not using postfix, but still sending through a relay. I've never used it.

As for setting the FROM header, that can be anything.  FROM isn't authenticated, which is why we used to send emails using really funny "FROM" addresses in the old days. Anti-spam stuff changed that. If you are using a FROM from a domain that you own, no problem. If you attempt to use a FROM from another domain, some anti-spam techniques deployed by admins might prevent that.  For example, I use SPF DNS txt records to let other email servers know never to accept emails with my domains that aren't from my SMTP server. By using an authenticated connection over 587/tcp to the gateway, my clients CAN send emails.

Sometimes an ISP forces the use of their SMTP relays from their subnet on 25/tcp.  That could be unauthenticated, but may have changed. I recall 15 yrs ago doing something like that. 

Hope this is helpful.

---

