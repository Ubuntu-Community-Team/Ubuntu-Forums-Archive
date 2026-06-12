---
title: "Where are my files"
date: 2011-06-21
forum: Ubuntu One (CLOSED)
---

### Post by McHenry on 2011-06-21
PC1 syncs Ubuntu One folder to server

Ubuntu One Web interface shows the files as synced

PC2 syncs Ubuntu One folder however only some of the files appear locally

---

### Post by duanedesign on 2011-06-23
On PC2 can you open a Terminal and run the command:

```
u1sdtool --waiting | wc -l
```

This will tell us how many files are waiting to be synced. We can see if PC2 knows about these missing files and is just slow to sync them or maybe something else.

---

### Post by McHenry on 2011-07-08
Problem is nothing is displayed as waiting in the queue.

U1 indicates that the file sync is up to date.

Interestingly there are many files on PC1 that are not appearing on PC2, however if I rename on of these files it then gets synced and appears on PC2 !!

Thanks.

---

### Post by mujahied on 2011-07-10
any one has more info abt this ubuntu one

---

### Post by duanedesign on 2011-07-14
> **McHenry said:**
> Problem is nothing is displayed as waiting in the queue.

U1 indicates that the file sync is up to date.

Interestingly there are many files on PC1 that are not appearing on PC2, however if I rename on of these files it then gets synced and appears on PC2 !!

Thanks.

Their was a bug with some users experiencing resuming uploads failing. Sounds like this may be what you are experiencing. Removing the file from the Ubuntu One (or UDF) directory and then moving them back resulted in them being uploaded. IN your case renaming might of accomplished the same thing. I think the bug was fixed. Can you make sure your client is updated.
```
sudo apt-get update; sudo apt-get upgrade
```

---

