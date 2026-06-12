---
title: "Postfix and Dovecot missing sockets?"
date: 2009-04-30
forum: Server Platforms
---

### Post by Dy1anW on 2009-04-30
So, I was trying to set up a virtual mail system using MySQL, Postfix, Dovecot, et al. based on [this how-to](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/) by Johnny Chadda.

So far the biggest problem I've had is that I can't receive emails.  From logs I get this:
deliver(me@mydomain.com): 2009-05-01 02:01:15 Error: Can't connect to auth server at /var/run/dovecot/auth-master: No such file or directory

Sure enough, auth-master does not exist at all, and neither does the socket for postfix.  Here's a couple snippets from dovecot.conf:

protocol lda {
  postmaster_address = [email]postmaster@mydomain.com[/email]
  sendmail_path = /usr/lib/sendmail
  auth_socket_path = /var/run/dovecot/auth-master
}
...
master {
  path = /var/run/dovecot/auth-master
  mode = 0660
  user = vmail
  group = mail
}
client {
  path = /var/spool/postfix/private/auth
  mode = 0660
  user = postfix
  group = postfix
}

From having done extensive searches on numerous sites (including dovecot.org) I get the impression that auth-master is supposed to come with the dovecot package (bundled with 9.04), and there are several posts in other forums that mention people connecting to it.  Right now I can't find any information on auth-master, what code it's supposed to contain, or anything.

Any information would be greatly appreciated.

---

### Post by Dy1anW on 2009-04-30
Nevermind, I just ditched the whole Dovecot setup and went with Courier IMAP instead; the setup turned out to be infinitely easier.  Can receive mails now (haven't checked using a proper client yet).  All that remains is to tweak the overzealous filters so it's just spam that gets blocked.

[http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html)

---

