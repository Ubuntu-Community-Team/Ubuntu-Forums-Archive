---
title: "How to check for expired accounts"
date: 2008-11-13
forum: Security
---

### Post by rosv on 2008-11-13
Hi,
I'm about to write a bash script that deletes expired user accounts. The only problem is that I don't know how to check for account expiration.

Any ideas?

---

### Post by rosv on 2008-11-13
I think I got it.

Extract the value from the 8:th column in the /etc/shadow file (days since Jan 1, 1970 that account is disabled i.e. an absolute date specifying when the login may no longer be used).

Then you compare the current date to the 8:th column value. I the current date value is higher, the account is expired and will be dropped.

Or may there's a better to solution?

---

