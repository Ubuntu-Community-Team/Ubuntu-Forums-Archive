---
title: "Cannot copy contacts from Personal addressbook to CouchDB addressbook"
date: 2010-03-17
forum: Ubuntu One (CLOSED)
---

### Post by reidi on 2010-03-17
Ubuntu Karmic 9.10, fully up-to-date.
Typical Intel-based PC, a few years old.

I cannot copy contacts from my "On this computer" Personal addressbook to my "CouchDB" Ubuntu One addressbook.

I get the Evolution error: "Error adding contact.  Other error".  I used to be able to do this.  Interestingly I can manually add new contacts to the CouchDB Ubuntu One addressbook, and I can copy from the CouchDB Ubuntu One addressbook to the Personal addressbook, just not the other direction.

It seems that somehow I have broken something in the desktop-couch database configuration, but I can't sort it from the logs.

I have searched high and low in Ubuntu Forums and using Google, and tried a number of suggestions, but nothing has worked.

---

### Post by joshuahoover on 2010-03-17
> **reidi said:**
> Ubuntu Karmic 9.10, fully up-to-date.
Typical Intel-based PC, a few years old.

I cannot copy contacts from my "On this computer" Personal addressbook to my "CouchDB" Ubuntu One addressbook.

I get the Evolution error: "Error adding contact.  Other error".  I used to be able to do this.  Interestingly I can manually add new contacts to the CouchDB Ubuntu One addressbook, and I can copy from the CouchDB Ubuntu One addressbook to the Personal addressbook, just not the other direction.

It seems that somehow I have broken something in the desktop-couch database configuration, but I can't sort it from the logs.

I have searched high and low in Ubuntu Forums and using Google, and tried a number of suggestions, but nothing has worked.

I'm sorry to hear you're having problems copying contacts from your personal address book to your Ubuntu One address book. It sounds like we might benefit from getting a bug report. Please follow these steps so that we get useful debug information that will help us get to the bottom of this issue:

[LIST=1]
[*]File a new bug at: [https://bugs.edge.launchpad.net/evolution-couchdb/+filebug](https://bugs.edge.launchpad.net/evolution-couchdb/+filebug)
[*]Please be sure to provide the steps you're taking and the results (including any errors) you're getting
[*]Open Applications->Accessories->Terminal, and  run: 

[LIST]
[*]evolution --force-shutdown /usr/lib/evolution/evolution-data-server-2.28  > ~/evolution_debug.log 
[/LIST]
[*]Applications->Internet->Evolution Mail 
[*]Try to reproduce bug  and then attach ~/evolution_debug.log to the bug you filed
[/LIST]
Thank you,

Joshua

---

### Post by reidi on 2010-03-18
Thanks for your reply,  This has been filed as:

"Cannot copy contacts from Personal addressbook to CouchDB addressbook"

evolution-couchdb / Bugs / Bug #540675

---

### Post by joshuahoover on 2010-03-19
> **reidi said:**
> Thanks for your reply,  This has been filed as:

"Cannot copy contacts from Personal addressbook to CouchDB addressbook"

evolution-couchdb / Bugs / Bug #540675

Thank you for taking the time to file this bug and including all the information you did! Someone on the Ubuntu One team is looking into it and will follow up in the bug report.

Thank you,

Joshua

---

### Post by sujith_s80 on 2010-10-28
I am still facing this issue.I am not able to sync up with the ubuntu one address book using Evolution mail client.

Can anybody let me know the update on this ?

---

