---
title: "Update Manager Issue"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by TheMixtureMedia on 2013-04-25
Hi there when I try to update in terminal I get this issue

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

Can someone help

---

### Post by grahammechanical on 2013-04-25
This is the command that I used in this situation

```
sudo rm /var/lib/apt/lists/* -rf
```

It removes (rm) deletes all the scripts in the lists directory. To replace them run ```
sudo apt-get update
```

One of the scripts in the lists folder has a blank line to the top and Update Manager expects to find a header at the top.

Regards.

---

