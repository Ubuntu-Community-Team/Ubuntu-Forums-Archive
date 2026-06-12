---
title: "pop3/imap/greylisting"
date: 2006-09-21
forum: Server Platforms
---

### Post by mega on 2006-09-21
Do any of the email servers standard in the repo's support greylisting?

I'm using hmailserver now, but I need to switch the mail to my linux box, I have ~45,000 emails I access via imap

greylisting has almost completely rid my email from spam, so I dont want to loose this

sugestion?

---

### Post by Child of Wonder on 2006-09-21
You can use Postfix as your MTA and apt-get install postgrey.

---

### Post by mega on 2006-09-21
seems I have postfix installed already

is there a good howto for postfix?  I loved hmail because there was no file editing by hand, everything was gui and it works great

but I'm going though DIACAP/DITSCAP so I need to get all the non gov data off the servers that touch gov data

---

### Post by Child of Wonder on 2006-09-21
Sure, there are a lot of How Tos out there for Postfix.

Are you needing virtual accounts?  Want them to authenticate to MySQL DB?  LDAP?

You can use Dovecot or Courier for IMAP.  Both work well and are easy to use.  I'd personally recommend Dovecot.

---

