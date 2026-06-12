---
title: "Folders sync but files don't"
date: 2010-04-16
forum: Ubuntu One (CLOSED)
---

### Post by krackersk on 2010-04-16
Hi All,

I'm using Lucid and trying to get ubuntu one to work on my netbook. The system is up to date as I update every day. This is my problem:

In my ubuntu one folder, the folder structures syncs correctly but all the folders are empty, The files never sync.

This is what works:
Ubuntu one preferences has the right account and says:
"Synchonrisation in progress..."
Tomboy notes sync
The folders are there in my ubuntu one folder (as I mentioned above)

After a little digging I started using u1sdtool to get some more info, here is what I get:

```
$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH
```

```
$ u1sdtool --current-transfers
Current uploads: 0
Current downloads: 0
```

But it should be downloading as I've got 24gb left to download!!!

Appriciate any help on finding out what is going on

---

### Post by joshuahoover on 2010-04-16
> **krackersk said:**
> Hi All,

I'm using Lucid and trying to get ubuntu one to work on my netbook. The system is up to date as I update every day. This is my problem:

In my ubuntu one folder, the folder structures syncs correctly but all the folders are empty, The files never sync.

This is what works:
Ubuntu one preferences has the right account and says:
"Synchonrisation in progress..."
Tomboy notes sync
The folders are there in my ubuntu one folder (as I mentioned above)

After a little digging I started using u1sdtool to get some more info, here is what I get:

```
$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH
```

```
$ u1sdtool --current-transfers
Current uploads: 0
Current downloads: 0
```

But it should be downloading as I've got 24gb left to download!!!

Appriciate any help on finding out what is going on

I'm sorry to hear Ubuntu One isn't working properly for you. The best way for us to troubleshoot this is to file a bug report and attach all your log files. You can do this doing the following:

1. File a new bug report, including the steps you took to get to where you are at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)
2. From a terminal session (Applications->Accessories->Terminal) run: tar -cjf ~/Desktop/syncdaemon-logs.tar.bz2 ~/.cache/ubuntuone/log/
3. Attach ~/Desktop/syncdaemon-logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by krackersk on 2010-04-16
Bug #565147 filed. Thanks Jushua. Mate you are all over these forums, keep up the good work.

---

### Post by joshuahoover on 2010-04-19
> **krackersk said:**
> Bug #565147 filed. Thanks Jushua. Mate you are all over these forums, keep up the good work.

Thank you for the kind words and your patience! We're looking into what is causing this (and other similar problems) right now. Currently, it seems like things are working properly on the client end but performance with uploads and downloads is not very good. In the end, you get the results you're seeing: Folders show up and u1sdtool -s shows things are running properly but files don't sync.  Again, we're looking into what is causing this and hope to have an answer soon.

Thank you,

Joshua

---

### Post by QwUo173Hy on 2010-04-29
I am also effected by this bug. If there is an ubuntu-bug command I can run to attach useful information to the report, I can do so. But my symptoms and u1sdtool output are identical to krackersk.

---

### Post by joshuahoover on 2010-04-29
> **jarlath said:**
> I am also effected by this bug. If there is an ubuntu-bug command I can run to attach useful information to the report, I can do so. But my symptoms and u1sdtool output are identical to krackersk.

OK, we made some serious changes (and hopefully improvements!) on the server side last night. Can you disconnect and reconnect to the service to see if files start syncing for you? Also note that if you have a lot of files (say, hundreds) to sync, it may take quite a while. This is problem we're going to tackle next but will require updates on the client as well as the server side.

Thank you,

Joshua

---

### Post by bryceowen on 2010-04-29
Just wanted to throw in that I am also suffering from this problem. I just slicked and reinstalled Lucid this morning because of a different U1 problem. Now I've connected and got the empty folders.

I'm using the desktop version of Ubuntu, however. (Don't think that matters in this case.)

Half tempted to go back to Karmic...

---

### Post by QwUo173Hy on 2010-04-29
I'll let you know how it goes.

---

### Post by bryceowen on 2010-04-30
Just booted my machine this morning and checked my U1 folder to see if it wanted to start syncing files.

Now, all the folders have the green check on them, but still empty. (All day yesterday, they had the gray ! with the syncing icon.)

As a side note, I can't get to one.ubuntu.com/dashboard to even access my files. (Makes me doubly glad I had the foresight to back everything up to a flash drive before I started this little adventure.)

I'm thinking I'll have to deal without U1 for the first couple weeks to let the kinks get worked out.

---

### Post by QwUo173Hy on 2010-04-30
> **joshuahoover said:**
> OK, we made some serious changes (and hopefully improvements!) on the server side last night. Can you disconnect and reconnect to the service to see if files start syncing for you? Also note that if you have a lot of files (say, hundreds) to sync, it may take quite a while. This is problem we're going to tackle next but will require updates on the client as well as the server side.

Thank you,

Joshua
Joshua, it seems to be working now. Thank you!

---

### Post by pp12345 on 2010-04-30
I also still suffer form a very similar error ( files appear in the web interface but are not synced).
I tried to upload a big source tree ( git repository with hundreds of commits) + hundreds of files.

---

### Post by Slorg on 2010-04-30
Looks like I have the same problem, here for more details:
[http://ubuntuforums.org/showthread.php?p=9202720#post9202720](http://ubuntuforums.org/showthread.php?p=9202720#post9202720)

---

### Post by Slorg on 2010-04-30
Ah, it looks like everything is synced now.:biggrin:
It just takes really, really, really long..

---

### Post by joshuahoover on 2010-04-30
> **Slorg said:**
> Ah, it looks like everything is synced now.:biggrin:
It just takes really, really, really long..

Yep, apologies for the poor performance. We're working hard on remedying the issues. Follow us at [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone) for updates. And thanks to everyone for your support and patience!

Joshua

---

