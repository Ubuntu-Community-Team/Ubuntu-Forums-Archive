---
title: "fetchmail and sendmail on ubuntu"
date: 2008-01-03
forum: Server Platforms
---

### Post by naugiedoggie on 2008-01-03
Hello,

On my old system (Slackware), I had fetchmail and sendmail working with virtusertable and fetchmail multidrop so that if a message came in for a user not in virtusertable, it would be rejected by sendmail and in that case, fetchmail just drops the message (/dev/null it).  

I cannot recreate this on ubuntu.  the same fetchmail rcfile and the same virtusertable &c in sendmail -- i copied them over.  But sendmail accepts every message offered by fetchmail.

Because I handle all my own mail, I get thousands of spam messages an hour.  I cannot afford to have sendmail processing each of these.  The old setup was perfect for dumping everything that arrived for delivery to some nonsense name.

Perhaps, someone can tell me what ubuntu is doing differently with sendmail.  I've been over the docs and I can't see it.  My virtusertable has a list of all valid users and then this is the last entry:

@trollope.org   error:nouser user unknown

running sendmailconfig generates no errors.

Please note that changing mail systems is not a solution.

Any help would be appreciated.

Thanks.

mp

---

