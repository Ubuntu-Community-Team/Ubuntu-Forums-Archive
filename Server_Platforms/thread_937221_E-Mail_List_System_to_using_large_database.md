---
title: "E-Mail List System to using large database"
date: 2008-10-03
forum: Server Platforms
---

### Post by lopes_andre on 2008-10-03
Hi,

I need to setup a E-Mail List(newsletter) System using my Ubuntu server. 

Wich is the best option for large lists?


Best Regards, Andre.

---

### Post by Dr Small on 2008-10-03
Have you looked at mailman?

---

### Post by lopes_andre on 2008-10-04
Hi, 

The Subscribers List in Mailman is inside database(Mysql)?

I need a system that uses a database to support the Subscribers List.


Best Regards, Andre.

---

### Post by schettj on 2008-10-04
Why?

Anyway, another vote for mailman... once you get it set up (somewhat non-trivial, as you need to muck about with alias in your email server) it's very feature rich, and sorta "the standard" for these things.

If you want to "import" emails from a database into mailman, that's relatively simple once the list is set up (mass subscription, from a file... so you export your email list from your database to a text file, then use that mass-subscribe function in mailman.)

---

### Post by Dr Small on 2008-10-04
> **schettj said:**
> Why?

Anyway, another vote for mailman... once you get it set up (somewhat non-trivial, as you need to muck about with alias in your email server) it's very feature rich, and sorta "the standard" for these things.

If you want to "import" emails from a database into mailman, that's relatively simple once the list is set up (mass subscription, from a file... so you export your email list from your database to a text file, then use that mass-subscribe function in mailman.)
Why does your mailing list need to use a database (mysql)?
Mailman is simple to use, and I have seen some fairly large mailing lists out there.

---

