---
title: "PostgreSQL Security Question / Problem"
date: 2010-06-21
forum: Server Platforms
---

### Post by Geoff918 on 2010-06-21
```
sudo -u postgres psql
could not change directory to "/home/user"
```I get this error when I launch psql. Clearly it's because the postgres user does not have privileges to access my "root" user's account.

So my question is this: What should I do from a security perspective?
a) Provide write access to the user Postgres to my directory (seems risky)
b) Create a Postgres user (not sure how that would impact security)
c) Some option I'm not yet aware of or considering

I have about a year of Ubuntu experience and I'm not terrible with it. But, I'm working with some sensitive data here. I have locked down the computer from outside access with a couple of external firewall layers and restrictive permissions on the software firewall. Further, PostgreSQL is designed to not permit access from external machines without tweaking the default settings.

The "root" user that is being used above has some good restrictions. The home directory has been switched away from world readable and world writable.

That said, I want to make my system more secure but not so secure that it becomes cumbersome to use. (I have some experience with OpenBSD and it's pretty great but can be a real pain at the same time).

Thanks for any help!

Geoff

---

### Post by Geoff918 on 2010-06-21
To solve this problem I was instructed as follows by Nitsuga on #ubuntu on IRC Freenode:

> sudo -i -u postgres psql

That solved the problem!

---

