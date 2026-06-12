---
title: "Postfix - Prevent system accounts from receiving mail ..."
date: 2006-08-22
forum: Server Platforms
---

### Post by voidPtr on 2006-08-22
I noticed with the default install of Postfix, spammers could easily send e-mail to all of the various system accounts.  This is bad as if you give each user a 2GB mailbox, these system accounts could end up wasting 40GB (potentially) if saturated with spam.  

I'm curious how to deny certain users from receiving mail?  Right now I'm leaning towards altering the local_recipient_maps to point to a custom defined list instead of /etc/passwd.  I don't want to use virtual mailboxes or external quota mechanisms either.  

Honestly, I think this is sortof a bug.  The 20 something system accounts should not be able to receive mail by default!

-voidPtr

---

### Post by voidPtr on 2006-08-29
I'll answer my own question I suppose ...

local_recipient_maps = hash:/etc/postfix/mailusers $alias_maps

Then, create /etc/postfix/mailusers as a 2 column table (2nd column is not used but necessary) with the following format:

username@             blah
[email]username@domain.com[/email]   blah

If you want just the local name (not a specific domain name) be sure to append @ to the end, or it will not work.

Also, run postmap mailusers to create mailusers.db.

This is much quicker than creating a check_recipient_access blacklist if you have fewer than 20 users or so.

-voidPtr

---

