---
title: "I can't move a file."
date: 2010-11-06
forum: Security
---

### Post by NoSuchDevice on 2010-11-06
OK I am trying to move a folder to a restricted area and it says I need root access, how can I get root access I been trying for ages and searching Google does not help because I am so new to Ubuntu I don't know what command lines mean or anything.

---

### Post by uRock on 2010-11-06
Please check out this link to learn about sudo and root permissions. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can move the file using **sudo** in front of the **mv** command or using **gksudo nautilus** in a terminal to open nautilus with root permissions, but beware that making changes to the root file system can cause major problems.

---

### Post by Rubi1200 on 2010-11-06
> **uRock said:**
> Please check out this link to learn about sudo and root permissions. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can move the file using **sudo** in front of the **mv** command or using **gksudo nautilus** in a terminal to open nautilus with root permissions, but beware that making changes to the root file system can cause major problems.
+1

It would help if you told us what file you want to move, to where, and, importantly, why.

As uRock already mentioned, changes to the root file system can cause untold harm and complications.

---

