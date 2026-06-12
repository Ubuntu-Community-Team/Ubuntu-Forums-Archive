---
title: "Adding users to LDAP authentication"
date: 2009-07-09
forum: Server Platforms
---

### Post by hubie on 2009-07-09
I just know this is a really simple question, but I can't seem to find the answer.  I've set up a test server with LDAP authentication.  I've tested it and it seems to work great for logging in.  As a model, I found many many very nice resources on the web, as well as info from the LDAP O'Reilly book, that tell you how to set it up and migrate the accounts.  What I can't seem to find is how to add users after it is all set up.

Do I add users locally to the passwd file and rerun the migration scripts, or do I add the users to the LDAP database (and how then does their home directories get created)?  Is there a tool that does all this for me that I am unaware?  Also, I want to get Samba authenticating on LDAP (and later Radius).  Are there any subtleties to watch out for, such as having to run a special tool for each software package that uses LDAP when a new account is added?

---

