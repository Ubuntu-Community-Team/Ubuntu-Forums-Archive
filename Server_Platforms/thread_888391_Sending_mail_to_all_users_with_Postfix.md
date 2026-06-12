---
title: "Sending mail to all users with Postfix"
date: 2008-08-13
forum: Server Platforms
---

### Post by m_software on 2008-08-13
Hi,

I can't find a decent solution for my problem.

I'm using Postfix + mailx + Courier POP3 + Courier IMAP

Problem: I want to be able to sent an email to all Users. For example an email sent from "sender@localhost" to all user@localhost (e.g user1, user2, ...).

please Help me :(

---

### Post by jonabyte on 2008-08-14
I am not familiar with postfix, but would there be a distribution list that you can create that has all the users in it?

---

### Post by m_software on 2008-08-16
Thanks for reply jonabyte.

Yea but how?

---

### Post by jonabyte on 2008-08-16
got me, do you have webmin installed, its an easy way to make modifications to some of the server apps.

---

### Post by StickyStyle on 2008-08-16
You could setup Mailman for a mailing list and add everyone to a list [https://help.ubuntu.com/community/Mailman](https://help.ubuntu.com/community/Mailman)

Or you could could create an alias in /etc/aliases and make everyone you want a member of it...
```

allusers: user1, user2, user3, user4

```

---

### Post by gishaust on 2008-08-16
If you install postfixadmin it has a point where you can send all an email.

---

### Post by rivendale on 2009-05-26
> **m_software said:**
> Thanks for reply jonabyte.

Yea but how?

you go to 

/etc/aliases
file and edit it
add lines like 

all: user1, user2  etc

---

