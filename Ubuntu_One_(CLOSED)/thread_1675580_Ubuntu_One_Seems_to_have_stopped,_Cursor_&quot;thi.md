---
title: "Ubuntu One Seems to have stopped, Cursor &quot;thinking&quot;"
date: 2011-01-25
forum: Ubuntu One (CLOSED)
---

### Post by the_weekend on 2011-01-25
Hey Folks,
I accidentally started to sync a remote drive so I turned off syncing on that folder, moved the remote drive mount point and have been having problems ever since. I only have created one file in that folder since this happened and it's got a .u1conflict extension which I'd never seen. 
The cursor seems stuck "thinking" now.

I tried getting the log to record and didn't have any luck.
Help?

---

### Post by duanedesign on 2011-02-02
Could you please try the following steps to remove the folder that you accidentally added from the queue.

```
u1sdtool --list-folders
```
note the ID that is used by new UDF
```
u1sdtool --unsubscribe-folder=$ID
```
(where $ID = id that was received by running list-folders)
```
u1sdtool --quit 
```
this will quit the syncdaemon and drop the queue
```
u1sdtool --start 
```
this will start syncdaemon again, but do not connect
(open a new terminal, since this will not release the terminal right away)
```
u1sdtool --delete-folder=$ID
```
```
u1sdtool --connect 
```

thank you,
duanedesign

---

