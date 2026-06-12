---
title: "help setting up a mail server."
date: 2009-09-04
forum: Server Platforms
---

### Post by dave54321 on 2009-09-04
i just registered a domain and have setup an irc, web, ssh, ftp, database(oracle xe) and voip(murmur) server. now i would like to setup a pop (or imap) mail server and maybe later a smtp server. ive tried some tutorials and had no luck mainly because i dont know how postfix courier and mysql works.. 
what im asking for is an easy tutorial to setup a simple pop/imap server for like 5 emails
im running ubuntu 9.04 desktop edition like a server.
if anyone could give me a tutorial, thatwould be awsome

ps. this is my first time on ubuntu forums

---

### Post by zadehas on 2009-09-04
I highly recommend dovecot as imap / pop server instead of courier, it works great with postfix and mysql.
Here's a tutorial for this: [http://www.opensourcehowto.org/how-to/mysql/mysql-users-postfixadmin-postfix-dovecot--squirrelmail-with-userprefs-stored-in-mysql.html]("http://www.opensourcehowto.org/how-to/mysql/mysql-users-postfixadmin-postfix-dovecot--squirrelmail-with-userprefs-stored-in-mysql.html")
If you plan on hosting just 5 emails, you could avoid the complexities of setting up mysql based mailboxes and go for the basic system-accounts setup.

---

### Post by dave54321 on 2009-09-04
thanks i will try it right now!

---

### Post by Bachstelze on 2009-09-04
> **zadehas said:**
> I highly recommend dovecot as imap / pop server instead of courier, it works great with postfix and mysql.
Here's a tutorial for this: [http://www.opensourcehowto.org/how-to/mysql/mysql-users-postfixadmin-postfix-dovecot--squirrelmail-with-userprefs-stored-in-mysql.html]("http://www.opensourcehowto.org/how-to/mysql/mysql-users-postfixadmin-postfix-dovecot--squirrelmail-with-userprefs-stored-in-mysql.html")
If you plan on hosting just 5 emails, you could avoid the complexities of setting up mysql based mailboxes and go for the basic system-accounts setup.

What he said. ;) But I think you missed something. You will use an IMAP server (probably Dovecot) to make the users' mailboxes accessible from outside, but how will the mail arrive in their mailboxes in the first place?

---

### Post by zadehas on 2009-09-04
> **HymnToLife said:**
> What he said. ;) But I think you missed something. You will use an IMAP server (probably Dovecot) to make the users' mailboxes accessible from outside, but how will the mail arrive in their mailboxes in the first place?
Postfix handles that with maildrop by default - or at least I don't remember ever having to configure an extra MDA for use with postfix.

---

### Post by Bachstelze on 2009-09-04
> **zadehas said:**
> Postfix handles that with maildrop by default - or at least I don't remember ever having to configure an extra MDA for use with postfix.

Yeah, but there will probably be some Postfix config to be taken care of.

---

