---
title: "Bugzilla sendmail problem"
date: 2008-07-09
forum: Server Platforms
---

### Post by crimsondr on 2008-07-09
Hi all,

I just installed ubuntu 8.04 server with the bugzilla package.  When I enter in a bug and commit I get the following error:

```
undef error - Insecure dependency in exec while running with -T switch at /usr/share/perl5/Mail/Mailer/sendmail.pm line 22.
```

I've searched and cannot find a solution to the problem.

Any ideas?
Thanks.

---

### Post by vertigo23 on 2008-09-30
I believe this is the bug in bugzilla described here:

[https://bugzilla.mozilla.org/show_bug.cgi?id=340538](https://bugzilla.mozilla.org/show_bug.cgi?id=340538)

Any chance of getting this into Hardy?

EDIT: Ok, I looked at /usr/share/doc/bugzilla/changelog.gz and it's allegedly already patched.  However, my users are still getting the same error when committing bugs.  Plz to fix!!

---

