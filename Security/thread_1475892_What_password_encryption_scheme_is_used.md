---
title: "What password encryption scheme is used?"
date: 2010-05-07
forum: Security
---

### Post by Skaperen on 2010-05-07
I'm trying to determine password compatibility between /etc/{passwd,shadow} system users, and a separate password file for the dovecot imap package.  Turns out there are multiple different MD5 or SHA* based schemes.  Unfortunately, I can't just generate passwords under different password programs to determine if they are using the same scheme, because the random salt will make them different, anyway (so they could be the same scheme, but it will look like it is a different scheme).

---

### Post by Agent ME on 2010-05-07
I believe (going off memory, may be off a bit) that the entries in /etc/shadow follow the format of $*scheme number*$*salt*$*hash*

I might be mixing up the salt and hash's locations, but if the first part (the scheme/algorithm number) is the same, it should be using the same system. Note that many systems like ubuntu support using many algorithms, but generally when making a new user account will use the same one.

---

### Post by Bachstelze on 2010-05-07
What Agent ME said. See [font=monospace]man crypt[/font] for details.

---

