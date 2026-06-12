---
title: "Right click syncronize on one not working"
date: 2011-01-31
forum: Ubuntu One (CLOSED)
---

### Post by MechaMechanism on 2011-01-31
When I right click a folder and select synchronize it does not sync.  It continues to say synchronize on one.  When I selected my music folder back in December it worked, but now it doesn't.  It continues to work for the music folder and 1 other folder.  I can't simply add my documents folder.

How do I force one to sync my documents folder.

---

### Post by duanedesign on 2011-02-01
If the right-click in Nautilus is not working could you please try the u1ssdtool command from the command line.

If you want to add a folder to Ubuntu One then you will need to use **u1sdtool --create-folder** option. This operation can take some time and even timeout but in fact the request was added to the metadata queue. Open a Terminal and try:

```
 u1sdtool --create-folder=/home/rtg/Music/
```

(you might want to look at metadata queue)

```
 u1sdtool --waiting-meta
 CreateUDF
```

When UDF is created your files will start syncing from that folder.

You can see what folders are synced to Ubuntu One using **u1sdtool --list-folders** switch:

```
 u1sdtool --list-folders
Folder list:
  id=20b0b044-523f-462a-8938-7e2fa16030b0 subscribed=True path=/home/rtg/Public
  id=3c928fd5-295a-480f-9dee-88aaca05d33a subscribed=True path=/home/rtg/Music
  id=a19bb966-a0e9-4f05-a927-f9fc81986258 subscribed=True path=/home/rtg/.ubuntuone/Purchased from Ubuntu One
  id=5577d808-6a3f-4873-8b27-1fd644bd7e20 subscribed=True path=/home/rtg/Documents
```

If you no longer want to sync the folder to Ubuntu One you can remove the UDF via **u1sdtool --delete-folder**. Please use the folder ID that is printed by **u1sdtool --list-folders**. This command does not delete anything from your filesystem but the corresponding folder will be removed from your cloud storage

```
 u1sdtool --delete-folder=3c928fd5-295a-480f-9dee-88aaca05d33a
```

---

### Post by MechaMechanism on 2011-02-01
```
u1sdtool --waiting-meta
nothing is printed out
``````
u1sdtool --create-folder=/home/nate/Documents/
FolderCreateError: UDFs can not be nested (path=/home/nate/Documents)
```Seems theres a bug report on it.
[https://bugs.launchpad.net/ubuntuone-client/+bug/649945](https://bugs.launchpad.net/ubuntuone-client/+bug/649945)

```
u1sdtool --list-folders
Folder list:
  id=755fad73-b0bd-4c67-8604-98c645564b92 subscribed= path=/home/nate/Documents
  id=1b190e02-53c1-46d0-8517-b21bf8bedc3d subscribed=True path=/home/nate/Music
```Seems like the folder Documents is already subscribed.  Just not syncing.

I tried adding my pictures folder as well but nothing is printed out with u1sdtool --waiting-meta

---

### Post by Carson5696 on 2011-02-01
Is your account linked sometimes they dis-link

---

### Post by Carson5696 on 2011-02-01
try restarting your computer

---

### Post by MechaMechanism on 2011-02-01
Ah ha, I just noticed that one of the folders does not have true in it.

```
id=755fad73-b0bd-4c67-8604-98c645564b92 subscribed= path=/home/nate/Documents
```The subscribed= is missing the true.  So how do I get it to have true after =.

---

### Post by duanedesign on 2011-02-02
Yes you are right. When it shows nothing that means subscribed=False.

To subscribe the folder use the command:

```
u1sdtool --subscribe-folder=FOLDER_ID
```

in your case the command would be

```
u1sdtool --subscribe-folder=755fad73-b0bd-4c67-8604-98c645564b92
```

---

### Post by MechaMechanism on 2011-02-04
> **duanedesign said:**
> Yes you are right. When it shows nothing that means subscribed=False.

To subscribe the folder use the command:

```
u1sdtool --subscribe-folder=FOLDER_ID
```in your case the command would be

```
u1sdtool --subscribe-folder=755fad73-b0bd-4c67-8604-98c645564b92
```
I did this and now my documents and pictures folders are shown as true.  But, the ubuntu-one-sync daemon was causing high cpu usage.  I killed the one-sync daemon.  How do I restart the daemon.

---

