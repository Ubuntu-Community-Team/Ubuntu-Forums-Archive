---
title: "Postfix/Virtual Domains/Squirrelmail   IMAP required?"
date: 2006-08-10
forum: Server Platforms
---

### Post by prozach on 2006-08-10
postfix with Virtual Alias Domain.  All users are local users.  Theres really only two of us and we use squirrelmail exclusively on the current server(lots of aliases + multiple domains).

My question is do I really need to setup an IMAP server?  I don't want to use maildirs and would prefer to stick to the /var/mail style(makes for a simple migration from the existing sendmail based server), I got the impression that I need to switch to the maildir style if I use courier and most of the howtos use courier.  Am I misinformed?  Since we're using squirrelmail and or mutt, I don't plan on adding POP3 support....just trying to understand the relationships between the various services and daemons.

So far things are going well and I really like postfixadmin.  just taking my time to really understand things as I go.

-Zach

---

### Post by prozach on 2006-08-10
I did a little more digging.  Looks like I do have IMAP on my current system (UW-IMAP).

In researching the differences between mbox and maildir I have come to the conclusion that maildir is better and will be converting and installing courier....also learned why my current system is so slow when it comes to email.

-z

---

### Post by MJN on 2006-08-11
I would recommend you check out Dovecot ([www.dovecot.org)]("http://www.dovecot.org) for") for your IMAP server. Dead simple, dead easy to use (works straight out of the box for a standard install), fast, small footprint etc etc.
 
Mathew

---

