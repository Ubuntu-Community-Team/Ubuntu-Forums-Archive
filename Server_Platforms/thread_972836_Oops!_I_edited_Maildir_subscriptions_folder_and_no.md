---
title: "Oops! I edited Maildir subscriptions folder and now its broken"
date: 2008-11-06
forum: Server Platforms
---

### Post by Mark F on 2008-11-06
I use Roundcube to access mail via Dovecot. It let me include an "&" in a folder name and then I couldn't delete the folder later via Roundcube. I had a look in the ~/Maildir/subscriptions file and found the offending entry and deleted it. While I was in there I moved a few things around to "tidy up" the order of entries. Now I can only see the INBOX folder via Roundcube. When I go into "preferences" all of the "subscription" checkboxes are unchecked and when I check them all, it won't save. 

Suggestions for an idiot please!

---

### Post by Mark F on 2008-11-06
Sussed it. Moved subscriptions to subscriptions.bak then went back in via Roundcube and reactivated subscriptions checkboxes. This recreated the file "subscriptions" in the Maildir. Phew!

---

