---
title: "move folder contents to /var/www/web folder"
date: 2019-07-26
forum: Server Platforms
---

### Post by Heeter on 2019-07-26
Hi all,

I downloaded some update files and subfolders to upgrade a current website from one version to the next.

I downloaded and unzipped the files into a single folder in the /tmp folder

I would like to straightup move all the files and subfolders in the current /tmp/upgrade folder to the /var/www/web folder

The "**mv /tmp/upgade/* /var/www/web**" is just moving the files, but refuses to move all the subfolders, complaining that they are not empty.

What is a better command to complete this?

Regards

---

### Post by Heeter on 2019-07-26
DUH!!!!

Sorry Guys, totally forgot about the rsync 

Got it going now, Thanks

Regards

---

### Post by TheFu on 2019-07-26
**rsync** is what I'd use, but there are many caveats for swapping in new website for old, depending on if it is static files or a webapp. 
Also, with better planning, you could have moved the old version to a new directory-name, then created the new files directly where you need them. Whether that is a good idea or not depends. At this point, restoring from a backup before the first attempt might be needed.

Most webapps have a requirement that the DBMS schema be updated when the code changes. Each should document how to accomplish that task.

---

