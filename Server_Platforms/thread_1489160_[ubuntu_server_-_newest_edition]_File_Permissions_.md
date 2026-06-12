---
title: "[ubuntu server - newest edition] File Permissions Won't Change/Wrong One"
date: 2010-05-20
forum: Server Platforms
---

### Post by gggccc on 2010-05-20
I am running the newest version of ubuntu server. I can't get file permissions to change or I just don't know which one to set it on for website data. I can view the data, but wordpress gives me "failed" and "go to codex for help" errors about changing/uploading data. What file permission setting do I have to put it on or what am I doing wrong?

---

### Post by cariboo on 2010-05-22
Files and directories in /var/www should be owned by www-data:www-data and have a permission of 755.

---

### Post by gggccc on 2010-05-22
Now I get errors when uploading files. 
(That always happened)
The "Update  File" button is now working though.

---

