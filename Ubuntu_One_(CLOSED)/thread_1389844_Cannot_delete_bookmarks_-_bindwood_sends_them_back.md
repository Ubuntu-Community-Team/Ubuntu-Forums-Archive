---
title: "Cannot delete bookmarks - bindwood sends them back"
date: 2010-01-24
forum: Ubuntu One (CLOSED)
---

### Post by JoeWheeler on 2010-01-24
So I love ubuntu one. The only problem is I'm having trouble with Bindwood, the bookmark synchronising program. I'm on 9.10 and using firefox and whenever I try and delete a bookmark it just appears in my bookmarks next time I restart firefox. Any help?

---

### Post by joshuahoover on 2010-01-25
> **JoeWheeler said:**
> So I love ubuntu one. The only problem is I'm having trouble with Bindwood, the bookmark synchronising program. I'm on 9.10 and using firefox and whenever I try and delete a bookmark it just appears in my bookmarks next time I restart firefox. Any help?

Hi Joe! Can you try installing a newer version of Bindwood and if you still have problems, please file a new bug at [https://bugs.edge.launchpad.net/bindwood/+filebug?](https://bugs.edge.launchpad.net/bindwood/+filebug?) and attach the following log file to the bug report: *~/.cache/desktop-couch/log/desktop-couch-replication.log* Here is how you can get the new version of Bindwood that fixes some issues:

[LIST=1]
[*]Quick Firefox
[*]Open* System->Administration->Software Sources*
[*]Click the *Third Party *tab
[*]Click the *Add *button
[*]Paste the following: deb [http://ppa.launchpad.net/urbanape/bindwood-exp/ubuntu](http://ppa.launchpad.net/urbanape/bindwood-exp/ubuntu)karmic main
[*]Click the *Add Source* button
[*]When prompted, click the *Reload* button
[*]Open *Applications->Accessories->Terminal*
[*]Run the following commands:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0x345dbd6f5eda02212a67b49e368bb0c046f34169

sudo apt-get update
[*]Open Firefox and see if the problem persists
[/LIST]
Thank you,

Joshua

---

