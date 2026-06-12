---
title: "Lost contacts in Evolution, their still in database, how to fix"
date: 2010-05-16
forum: Ubuntu One (CLOSED)
---

### Post by MechaMechanism on 2010-05-16
EDIT:  SOLVED.  I have no idea how it happened but somehow it fixed itself.  The beam.smp has restarted and Evolution now has the address book Ubuntu One properly filled.




I lost my contacts from the Ubuntu One address book.  I had a error where it said my contacts would not be available until the restart of something or other.  I looked in the .local where the .html file is and browsed the database and it looks like their still in the database.  How do I get the contacts from database back into Evolution Ubuntu One address book?


EDIT:

Followed this page to fix it. Did not work.
[http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting](http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting)

> nate@universal-mechanism:~$ dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by sterilegenie on 2010-05-16
Well my contacts have disappeared a couple of days ago and have yet to return. This Ubuntu One thing is extremely flakey and will be moving my contacts out of couchdb and storing them locally from now on.

---

### Post by joshuahoover on 2010-05-17
> **sterilegenie said:**
> Well my contacts have disappeared a couple of days ago and have yet to return. This Ubuntu One thing is extremely flakey and will be moving my contacts out of couchdb and storing them locally from now on.

If your contacts disappeared this is a **VERY **serious issue that we (the Ubuntu One team) need to look into ASAP. We've disabled syncing with the server so it shouldn't be related to that at the moment. Can you please follow these instructions to provide us with some debug information in a bug report? 

[LIST=1]
[*]Applications->Accessories->Terminal, and  run: 
          tar cjf ~/desktop-couch_logs.tar.bz2 ~/.cache/desktop-couch/log


[LIST]
[*]evolution --force-shutdown /usr/lib/evolution/evolution-data-server-2.28  > ~/evolution_debug.log 
[/LIST]
[*]Open Applications->Internet->Evolution Mail 
[*]Try to reproduce the bug (whatever you were doing when you noticed your contacts "disappeared")
[*]File a bug at: [https://bugs.edge.launchpad.net/evolution-couchdb/+filebug](https://bugs.edge.launchpad.net/evolution-couchdb/+filebug)
[*]Attach the following files to the report:
~/evolution_debug.log
 ~/desktop-couch.logs.tar.bz2
[/LIST]
Thank you,

Joshua

---

### Post by MechaMechanism on 2010-11-05
> **joshuahoover said:**
> If your contacts disappeared this is a **VERY **serious issue that we (the Ubuntu One team) need to look into ASAP. We've disabled syncing with the server so it shouldn't be related to that at the moment. Can you please follow these instructions to provide us with some debug information in a bug report? 

[LIST=1]
[*]Applications->Accessories->Terminal, and  run: 
          tar cjf ~/desktop-couch_logs.tar.bz2 ~/.cache/desktop-couch/log
[LIST]
[*]evolution --force-shutdown /usr/lib/evolution/evolution-data-server-2.28  > ~/evolution_debug.log
[/LIST]
 
[*]Open Applications->Internet->Evolution Mail
[*]Try to reproduce the bug (whatever you were doing when you noticed your contacts "disappeared")
[*]File a bug at: [https://bugs.edge.launchpad.net/evolution-couchdb/+filebug](https://bugs.edge.launchpad.net/evolution-couchdb/+filebug)
[*]Attach the following files to the report:
~/evolution_debug.log
 ~/desktop-couch.logs.tar.bz2
[/LIST]
Thank you,

Joshua
Hi Joshua.  I filed a bug because it happened again.  I followed your instructions.
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/671507](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/671507)

---

