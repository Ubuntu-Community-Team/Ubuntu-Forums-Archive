---
title: "Confused - from address domain"
date: 2008-06-22
forum: Server Platforms
---

### Post by michellez on 2008-06-22
If I do a test to user2 from user1 via telnet on the mail server, fine... it appears to go from and to [email]user1@mylocal.doma[/email]in

In Squirrelmail if I do the same though it's going from/to @mail.externaldomain.com

Can't work out where the 2nd is coming from! :( I did have this domain in my postfix main.cf as 'myhostname'. Changed this to externaldomain.com and restarted Postfix though, with no change.

Confuzzled.

TIA,
Shell

---

### Post by michellez on 2008-06-22
Got it! Sorry.. Feel stupid.

SquirrelMail gets it from /etc/mailname

All sorted :)

---

