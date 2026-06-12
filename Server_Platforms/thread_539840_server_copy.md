---
title: "server copy"
date: 2007-08-31
forum: Server Platforms
---

### Post by moos3 on 2007-08-31
I'm trying to copy directories and databases daily from my development to my test box automatically. Any ideas on the best way to do this?

---

### Post by HermanAB on 2007-08-31
Use rsync over ssh with public keys and cron.daily.  Some googling and man page reading will get you going.

For the databases, you'll have to export the database, then rsync the exported copy.  You should not try to rsync a live database file, since the copy will be corrupted when the data changes on the original file.

'Hope that helps!

Herman

---

### Post by moos3 on 2007-08-31
Thanks. I was thinking rysnc just wasnt sure about the databases.

---

### Post by HermanAB on 2007-08-31
Yup, as someone said: Rsync is your friend.

(I even use it with Windoze using Cygwin and OpenSSH)

Cheers,

H.

---

