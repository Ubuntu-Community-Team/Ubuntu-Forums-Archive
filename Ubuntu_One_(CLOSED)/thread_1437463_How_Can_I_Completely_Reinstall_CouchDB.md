---
title: "How Can I Completely Reinstall CouchDB"
date: 2010-03-23
forum: Ubuntu One (CLOSED)
---

### Post by reidi on 2010-03-23
Ubuntu 9.10, fully up-to-date.
Standard Intel-based PC, a few years old.

I would like to completely remove the CouchDB database, and any couchdb settings in my profile.  Then I want to do a fresh reinstall.  The idea is to restore proper functionality with Evolution contacts, and with Ubuntu One.  These things used to work fine, and now don't.

I'm fine with the command-line, apt and editing configuration files.  I just want to make sure I remove all evidence of the current install, especially configuration specific to my login, before reinstalling.

If the only way to do this is via a reinstall of Karmic, then what personal configuration files related to CouchDB do I need to remove before doing that?

---

### Post by duanedesign on 2010-03-23
reidi,
there have been some server side errors lately related to couch. You might want to wait a day or two to see if gets fixed. I think i heard some fixes are being rolled out late tommorrow. 

You can look in your couchdb stdout..

```
gedit ~/.cache/desktop-couch/desktop-couchdb.stdout
```

...and see what kind of error you are getting. If you post any of that be careful your "token_secret" is in there. You can use the replace function on gedit to obfuscate those.

---

