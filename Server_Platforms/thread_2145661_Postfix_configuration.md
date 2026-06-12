---
title: "Postfix configuration"
date: 2013-05-16
forum: Server Platforms
---

### Post by robyone on 2013-05-16
Hi
I state thatI am not practical of Ubuntu and PostFix. TypicallyI use WindowsandMailEnable
I need to configure a mail server on Ubuntu with Webminand Postfix, butI can not figure out how to dothe following very simple things.
My need is to create a mail server with one or more domains, and one or more e-mail accounts for each domain: I need to activate the authentication of outgoing mail via username and password (the same as input) andbe able to send email from other host on the web, using the mailserver's host name
Therefore:
1.   Howcan Icreate a domain?(eg. pippo.com)
2.    How can Icreate a mailboxon adomain, withits password? (eg. [EMAIL="info@pippo.com"]info@pippo.com[/EMAIL])
3.    How can I setup the server so that it accepts theuse SMTP from any PC on the web?
4.    How can I set the outgoing mail authenticationwith the same credentials of theincoming? (address as username and password)
Can someone explain how to do? Preferably via the webmin interface for postfix, but that's okay also manuallyediting the configuration file.

---

### Post by CharlesA on 2013-05-16
This would probably help:
[https://library.linode.com/email/postfix/dovecot-mysql-debian-6-squeeze](https://library.linode.com/email/postfix/dovecot-mysql-debian-6-squeeze)

---

