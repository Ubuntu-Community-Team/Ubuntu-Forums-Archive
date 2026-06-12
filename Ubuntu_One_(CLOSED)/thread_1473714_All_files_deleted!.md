---
title: "All files deleted!"
date: 2010-05-05
forum: Ubuntu One (CLOSED)
---

### Post by alpha-buntu on 2010-05-05
Great guys... I really dont know what you are doing!!!

For weeks, one has been working great! now, since a week, files didnt sync at all.

since tuesday, it gotten better.

and today? this crappy service killed all files!!!! just GONE!!!!!!!!!! 

thanks to my previos experiences with other buggy webdav drives and other "online-destroy-your-data-harddrives" I made some backups.

just gone. wiped every file clean! maybe I should call ubuntu one: ubuntu one data shredder!

---

### Post by wilee-nilee on 2010-05-05
> **alpha-buntu said:**
> 
thanks to my previos experiences with other buggy webdav drives and other "online-destroy-your-data-harddrives" I made some backups.


Could it be that since this has happened before that it may be user error, hardware problems....etc.

---

### Post by japher on 2010-05-05
> **alpha-buntu said:**
> just gone. wiped every file clean! maybe I should call ubuntu one: ubuntu one data shredder!

Are they gone from your local machine only? Did you try the web interface at [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/) ?

---

### Post by joshuahoover on 2010-05-05
> **alpha-buntu said:**
> Great guys... I really dont know what you are doing!!!

For weeks, one has been working great! now, since a week, files didnt sync at all.

since tuesday, it gotten better.

and today? this crappy service killed all files!!!! just GONE!!!!!!!!!! 

thanks to my previos experiences with other buggy webdav drives and other "online-destroy-your-data-harddrives" I made some backups.

just gone. wiped every file clean! maybe I should call ubuntu one: ubuntu one data shredder!

This is a **VERY** serious problem. If you can join us on #ubuntuone on Freenode IRC, I can try to help troubleshoot this issue in real time. I'm joshuahoover on there and am normally on Monday-Friday, 13:00-21:00 UTC. 

A couple of questions:

[LIST=1]
[*]Are your files completely gone or are they marked as .u1conflict?
[*]Can you see the files via the web UI? ([https://one.ubuntu.com/files](https://one.ubuntu.com/files))
[/LIST]
Second, can you file a bug report by doing the following so that we can get some debug logs that will help us better understand what is going on and how we can fix this?

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[*]Attach all syncdaemon.log files (even those with dates in them) from this directory: ~/.cache/ubuntuone/log
[/LIST]
Thank you,

Joshua

---

