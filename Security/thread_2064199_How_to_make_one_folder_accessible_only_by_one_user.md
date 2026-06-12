---
title: "How to make one folder accessible only by one user"
date: 2012-09-28
forum: Security
---

### Post by harshal22 on 2012-09-28
I want to secure one folder e.g /media/disk/confidential
Only my account should have access to this folder and not other accounts should access this folder.
I have created other account which doesn't have administrative rights.
Given folder is on auto mounted file system (ext4).

Any help is appreciated.

---

### Post by cortman on 2012-09-28
You could run

```
sudo chown my_user /media/confidential
sudo chmod og-rwx /media/confidential
```

So that you own the folder and are the only one who can read, write, or execute files within it.

---

### Post by rookcifer on 2012-09-28
> **cortman said:**
> sudo chmod og-rwx /media/confidential[/CODE]


Or just:

chmod 0700 /media/confidential

But, OP, please note that file permissions only work when the other users don't have physical access to your box.  If they have physical access to your machine, all they have to do is boot a LiveCD and they can view any file.

In order to get real protection you need to encrypt that directory.

---

### Post by cortman on 2012-09-28
+1 for encryption- I encrypt my netbook's partitions for that very reason.

---

