---
title: "dovecot"
date: 2011-04-24
forum: Server Platforms
---

### Post by num on 2011-04-24
I got dovecot and webmin installed but i am confused as to how i add email addresses, i am using postfix as the smtp server. can someone please help?

i checked with dovecot's website but it is down and i am finding tutorials on how to setup dovecot but not add users, what am i missing here?

---

### Post by HermanAB on 2011-04-24
Howdy,

Dovecot is a mail delivery agent only.  It doesn't send mail.  It doesn't even receive mail. It only takes mail from a MTA like Postfix and makes it available to a mail client like Thunderbird.

So, if you want Dovecot to do anything useful, then you need to install Postfix or some such.  All mail receive and transmit are managed by Postfix.  If you did the default Postfix installation, then the mail users are system users, so to add a mail account, you need to add a system user account.  This is OK if the only thing the machine does is handle mail.

So, you got to do 'useradd' to add a mail account.

---

### Post by num on 2011-04-24
unfortunately in my case, the server is utilized as a file server for a local network, ftp server for remote computers, webserver and email server.

what do i do then?

also i will have to manage multiple domains as well, if i am setting up users on ubuntu to work with postfix, i have no way of separating out the domains.

---

