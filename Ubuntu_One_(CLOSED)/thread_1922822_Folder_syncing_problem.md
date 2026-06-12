---
title: "Folder syncing problem ?"
date: 2012-02-09
forum: Ubuntu One (CLOSED)
---

### Post by serfcx on 2012-02-09
If I sync a folder outside of the U1 folder by right click then the folder is shown as synced but none of the folders or files inside are synced.
If I take the items out of that folder to another folder and then return them to the folder then they sync.
Is this normal ?

---

### Post by duanedesign on 2012-02-10
Hi,
could you please try restarting all the Ubuntu One processes after adding the new ccloud folder. You can do this in a terminal with the commands:

```
u1sdtool -q

u1sdtool -c
```

The new cloud folder should start syncing. Their is a bug that prevents newly added folders from syncing until you restart Ubuntu One. this fix was supposed to already be released. We have escalated this issue to get the fix out asap.

---

### Post by serfcx on 2012-02-10
Thanks for the reply. Will try out.:D

---

