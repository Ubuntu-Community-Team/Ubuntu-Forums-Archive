---
title: "&quot;My synced folders&quot; won't sync :("
date: 2010-06-02
forum: Ubuntu One (CLOSED)
---

### Post by Potters Son on 2010-06-02
After trying time and time again to get a folder on my Desktop to sync with U1 (The menu entry "synchronize with Ubuntu One" wasn't doing squat and wouldn't be replaced with the stop sharing entry), I tried to take matters into my own hands:

```
u1sdtool --offer-share=/home/user/Desktop/catan user catan Modify
```

I think I did the wrong thing, but now the folder won't disappear, and it won't sync, either. (see attatched screenshot) :(

How on earth am I SUPPOSED to do this, anyway?

---

### Post by duanedesign on 2010-06-02
Right now sync performance is degraded. The U1 team is putting into place measures to fix this. We should start to see improved performance, hopefully, this week.

You can check which folders are 'User Designated Folders' set to sync by running the command:

```
u1sdtool --list-folders
```

Because of the slow performance right now the menu entry might not change to 'stop sharing' for awhile. If you want to get rid of a UDF from the commandline you can use the command.

```
--delete-folder=FOLDER_ID
```

FOLDER_ID you get from the --list-folders command

The command --offer-share is used to share a folder with other Ubuntu One users. So if you and me were working on a project, for instance, we could share a folder containing that project. You can run the following to see the list of 'shares'

```
u1sdtool --list-shares
```

You can reject the share with --reject-share=SHARE_ID. The SHARE_ID is returned by the --list-shares command.

**EDIT:** It does look like the catan folder on your desktop is set up to sync. You can see the number of items waiting to sync with the commands:
```
u1sdtool --waiting-metadata | wc -l
```
and
```
u1sdtool --waiting-content | wc -l
```
This number should get smaller over time. Take off the '| wc -l' to see more info about each item.

---

### Post by Potters Son on 2010-06-02
Weird. Thanks! I guess I'll just wait a week before I try an do anything else with U1.

---

