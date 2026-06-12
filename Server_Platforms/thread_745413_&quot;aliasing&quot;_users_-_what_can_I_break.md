---
title: "&quot;aliasing&quot; users - what can I break?"
date: 2008-04-04
forum: Server Platforms
---

### Post by hyper_ch on 2008-04-04
Hiho

I just wonder what can I break when I "alias" users by giving them the same UID?

Current situation:

I have setup a new user, changed his default shell to MySecureShell and chrooted him to /var/www/web21

Then I changed his UID to match the one of the user "web21" so that this new user can use his own login and be able to "edit" files as "web21".

---

### Post by MJN on 2008-04-05
In general it shouldn't pose a problem and is a perfectly valid situation. Most programs/functions utilise UIDs and not usernames, however, the potential problem is the word 'most' - some programs may utilise usernames and not UIDs and hence the consequences of this depends entirely on what those programs do with that info.

Mathew

---

