---
title: "Constantly uploading 10Kbps"
date: 2010-06-23
forum: Ubuntu One (CLOSED)
---

### Post by oshirowanen on 2010-06-23
Why is ubuntuone constantly uploading something at a rate of 10Kbps?  I am not even logged into it...

Smells a bit fishy.

I have deleted it completely just to stop the constant 10Kbps uploading, but still, I am interested to know what was being transmitted.

---

### Post by duanedesign on 2010-06-23
If you have set up Ubuntu One, depending on your version, it auto starts at boot. If I remember correctly you had to select 'start on launch' in Karmic. In Lucid if you have Ubuntu One set up it starts at boot.

Nothing should be uploading unless you have placed something in your Ubuntu One directory(or a UDF), or an application that uses desktopcouch is adding information to a CouchDB. A lot more apps are using couchDB for persistence. Gwibber, Lernid, bughugger to name a few.

Some logs to  look for more information about what the issue might be:

~/.cache/desktop-couch/log/desktop-couch-replication.log 
~/.cache/ubuntuone/log/syncdaemon.log


thank you,
duanedesign

---

