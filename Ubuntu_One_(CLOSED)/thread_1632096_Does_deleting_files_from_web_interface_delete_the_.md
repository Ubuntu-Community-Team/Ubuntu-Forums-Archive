---
title: "Does deleting files from web interface delete the files from the computer."
date: 2010-11-27
forum: Ubuntu One (CLOSED)
---

### Post by MechaMechanism on 2010-11-27
Does deleting files using the Ubuntu One web interface delete the files stored on my computer?

---

### Post by duanedesign on 2010-11-30
The sync is asynchronous, so anything added or removed from the server will also be added or removed from your computers.

However, you can remove a file from the Ubuntu One server and leave it untouched locally with the following steps:

```
u1sdtool --list-folders
```

get the folder ID of the folder you want to delete. Then use it in the following command:

```
u1sdtool --delete-folder=FOLDER_ID
```

thank you,
duanedesign

---

