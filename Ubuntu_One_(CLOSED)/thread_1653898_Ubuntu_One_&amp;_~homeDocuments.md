---
title: "Ubuntu One &amp; ~/home/Documents"
date: 2010-12-27
forum: Ubuntu One (CLOSED)
---

### Post by gunksta on 2010-12-27
Struggling a bit with Ubuntu One (U1). I have my account set up and my computer does connect to U1. The folders/files in ~/Ubuntu One/ seem to sync more or less as expected. However, ~/Documents/ is a mess.

The folder ~/Documents is selected to be synced with U1, but it never shows up on-line. Worse, new files are automatically given a .u1conflict extension, even though they can't possibly conflict with anything, because I created them only seconds ago and the name does not match anything else in the folder.

I think my problems started when I did some "spring cleaning" on the layout / structure of my folders. I was syncing everything from within ~/Ubuntu One/. Now I am trying to only keep a few things in this folder and selectively sync folders not in ~/Ubuntu One. This caused me to delete a bunch of links and generally futz with things and I may have accidentally caused some problems. 

```
u1sdtool --list-folders
```

Gives me:
```
Folder list:
  id=f11b8d60-777f-4dd5-901d-d438defd03ab subscribed=True path=/home/andy/Documents
  id=3c1f60f8-6c0d-49aa-98d8-142db1bd3740 subscribed=True path=/home/andy/Public

```

If anyone has any ideas as to why U1 automatically assigns new files as a conflict, I'm all ears. I am also interested in learning how to nuke my U1 account and start over. There aren't that many files. It shouldn't take more than an hour to upload the ~250 MB I'm trying to sync.

---

