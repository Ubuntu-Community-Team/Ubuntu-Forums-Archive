---
title: "Terminal server client licensing"
date: 2006-03-12
forum: Server Platforms
---

### Post by klen on 2006-03-12
Hiya,
I'm bit of a newb with linux but i'm getting in there\\:D/ 
Anyway i'm trying to find out how to delete terminal server license keys like you would on a windows box.

I'm trying to rdp into my windows box and today is the first day i can't...

---

### Post by ezHiker on 2006-03-12
Someone correct me if I'm wrong, but AFAIK Terminal Services CAL's are not stored on a Linux client, are tracked on the server by hostname and there is no legal way to immediately revoke an unused license.  After a certain amount of time (I can't remember how long), the unused CAL's expire and return to the pool, but this doesn't happen immediately.  I believe if you change the hostname of your Linux box, you will get a new 90-day temporary CAL, but you would have to do that again in another 90 days, and it wouldn't technically be legal anyways.  If you have unused CAL's, you can call Microsoft and have them reissue new ones for you.

Of course, you must have a CAL for each Linux client after the 90-day grace period expires.  This only applies to a server that is in Application Server mode.  If the Windows server is in Remote Administration mode, you don't need a CAL (but you are limited to 2 concurrent connections).

---

