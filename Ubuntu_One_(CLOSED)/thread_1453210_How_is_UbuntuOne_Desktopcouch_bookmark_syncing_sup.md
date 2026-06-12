---
title: "How is UbuntuOne Desktopcouch bookmark syncing supposed to work?"
date: 2010-04-12
forum: Ubuntu One (CLOSED)
---

### Post by reidi on 2010-04-12
How would I know if the bookmark syncing feature is working?  Where would I look in Firefox to see the synced bookmarks from my other systems?  Have looked pretty hard for the answer but it evades me.  Saw a reference to a couchdb.html, but it isn't on my system.

So, where are the synced bookmarks stored, and how do I view them in Firefox?
Thanks.

---

### Post by joshuahoover on 2010-04-13
> **reidi said:**
> How would I know if the bookmark syncing feature is working?  Where would I look in Firefox to see the synced bookmarks from my other systems?  Have looked pretty hard for the answer but it evades me.  Saw a reference to a couchdb.html, but it isn't on my system.

So, where are the synced bookmarks stored, and how do I view them in Firefox?
Thanks.

Good questions. :) Currently, bookmarks sync does not have a web UI component so it's tough to see that bookmarks are syncing properly. Right now, if you want to see if bookmarks are syncing you'd have to weed through the following log file: ~/.cache/desktop-couch/log/desktop-couch-replication.log We should have a web UI within the next couple of weeks. If you have multiple computers attempting to synchronize bookmarks, you should see the bookmarks from one computer on the other in the "Bookmarks" menu. We are about to release some important fixes to both the bookmarks sync and desktopcouch that will address some issues users may see with bookmarks and contacts not syncing properly. This should be out in time for Thursday's final freeze.

Thank you,

Joshua

---

