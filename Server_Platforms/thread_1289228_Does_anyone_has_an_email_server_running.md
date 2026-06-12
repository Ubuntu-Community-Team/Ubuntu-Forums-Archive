---
title: "Does anyone has an email server running?"
date: 2009-10-12
forum: Server Platforms
---

### Post by any.linux12 on 2009-10-12
Hey!

I starting an email server and I did the basic setup like Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail+Postgrey as in this thread  [http://ubuntuforums.org/showthread.php?t=97600&highlight=setup+a+mail+server](http://ubuntuforums.org/showthread.php?t=97600&highlight=setup+a+mail+server) by flurdy (thanks by the way)


It wasn't hard to set up but I didn't get how I can add users and stuff like that. I need to know if there is any content manager for email servers or if I have to use the database. Then my goal is to connect to that email server with evolution and using smtp I guess

any help please...thanks

---

### Post by epsolon77 on 2009-10-12
> **any.linux12 said:**
> Hey!

I starting an email server and I did the basic setup like Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail+Postgrey as in this thread  [http://ubuntuforums.org/showthread.php?t=97600&highlight=setup+a+mail+server](http://ubuntuforums.org/showthread.php?t=97600&highlight=setup+a+mail+server) by flurdy (thanks by the way)


It wasn't hard to set up but I didn't get how I can add users and stuff like that. I need to know if there is any content manager for email servers or if I have to use the database. Then my goal is to connect to that email server with evolution and using smtp I guess

any help please...thanks

I hate to move you in a different direction, but I set up Citadel for mail ([http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)).  This includes a built in webmail feature, as well as web based user management.  

I could be very wrong, but I think most of the packages you spoke up manage users from the command line.  I haven't used them because of this impression though, so please someone correct me if I'm wrong.

---

### Post by any.linux12 on 2009-10-12
> **epsolon77 said:**
> I hate to move you in a different direction, but I set up Citadel for mail ([http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)).  This includes a built in webmail feature, as well as web based user management.  

I could be very wrong, but I think most of the packages you spoke up manage users from the command line.  I haven't used them because of this impression though, so please someone correct me if I'm wrong.

but do you have an email server running?

---

### Post by i.r.id10t on 2009-10-12
Happily using ISPConfig for mail, web, dns,etc. for *many* domains on one box.  Using debian but there are howtos for using Ubuntu instead

---

### Post by Bachstelze on 2009-10-12
Running one (two actually), but they're totally different setups than yours (Sendmail, Dovecot, Horde).

---

### Post by nandemonai on 2009-10-13
I has one too :P

---

### Post by kpholmes on 2009-10-13
> **i.r.id10t said:**
> Happily using ISPConfig for mail, web, dns,etc. for *many* domains on one box.  Using debian but there are howtos for using Ubuntu instead

i was looking at using ispconfig but syscp was in the repositories so i installed that but its pretty challenging to use and i cant get any email servers working in it either. 

my setup is a debain aswell.

do you know of any good links to some tutorials explaining how to install ispconfig?

and how easy is it to set up ftp, web space and sub-domains? for users, and a mail server?

---

### Post by i.r.id10t on 2009-10-13
Set up is rather trivial, as long as you follow directions.  Once ISPConfig is installed you do all management via a web interface.  You can even let "clients" or "resellers" control their own stuff.

Configuring Debian to run it - [http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig2](http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig2)

And then just follow the ISPConfig instructions - [http://www.ispconfig.org/manual_installation.htm](http://www.ispconfig.org/manual_installation.htm)

---

### Post by epsolon77 on 2009-10-13
> **any.linux12 said:**
> but do you have an email server running?

Yes.  Citadel is a complete mail solution including both backed environments similar to sendmail ( don't know the actual app) and LDAP as well as web based system to manage, and read mail on.  I have also configured sendmail as a simple relay, but don't really use it (a test server sends automated email reports to me, I do not interface with the system.......ever)

---

