---
title: "Noob needs help with email server"
date: 2007-12-06
forum: Server Platforms
---

### Post by flyinggreg on 2007-12-06
Hi

I am pretty new at network admin and setup.  I got Ubuntu 6.06 Server running pretty good with a web-site.

I really need some help setting up an email server using Postfix & Postgresql.  I can find tutorials to setup with MySQL, but I need to set this up using PostgreSQL.  PostgreSQL is a dependency for other software I have running and don't want to run MySQL just for email.

Can someone please help?  I need to be able to run at least 2 seperate mailboxes, store messages on the server, and be accessible from any computer anywhere.

Thanks Ahead of Time!

---

### Post by now-new on 2007-12-06
I have this same question (I think) I want to know if its possible to run a mail server without running a hosting site, just a email server so I can have my email at home and can upload stuff from other computers and have it ready at home, or is there another way to do it easier?

---

### Post by ronald.higgins on 2007-12-06
> **now-new said:**
> I have this same question (I think) I want to know if its possible to run a mail server without running a hosting site, just a email server so I can have my email at home and can upload stuff from other computers and have it ready at home, or is there another way to do it easier?

Yep, you dont need to run a webserver.

You are going to have to look at a MTA firstly such as Postfix, Sendmail and there are others. 

Postfix is the more widely used and there is a a plethora of documentation on the net to get Ubuntu running with Postfix, here is a good place to start :

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

However if you want to use a web interface ala webmail you'll need to be running a webserver.

As for grabbing your mail via POP3 or IMAP take a look at Perdition, i've found it pretty easy to configure.

rH

---

### Post by flyinggreg on 2007-12-06
Yeah, I setup my server using the version for 6.06...with exception of installing MySQL.  Instead I installed PostgreSQL because I need it for SQL-Ledger.

I can find TONS of information for setting up email using MySQL, Postfix, and Courier; but no tutorials for  PostgreSQL, Postfix, and Courier....well, none for a newb.  I need the 'email servers for dummies using PostgreSQL, Postfix, and Courier' version.

I am learning the system admin as I go along...experience is the best teacher!

Thanks

---

